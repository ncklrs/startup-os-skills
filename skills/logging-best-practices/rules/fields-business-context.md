---
title: Capture Business Context
impact: HIGH
tags: fields, business, domain
---

## Capture Business Context

**Impact: HIGH**

Technical context alone is insufficient. Capture business-relevant data that enables domain-specific queries and debugging.

### Why Business Context Matters

> "Show me failed checkouts" is technical.
> "Show me failed checkouts for enterprise customers buying > $1000 with new checkout enabled" is **actionable**.

### Good Example: E-Commerce Context

```javascript
const event = {
  // ... required fields ...

  // === USER BUSINESS CONTEXT ===
  user: {
    id: "user_12345",
    tier: "enterprise",           // Subscription level
    account_age_days: 847,        // Tenure
    lifetime_value_cents: 2340000,// LTV
    orders_count: 47,             // Purchase history
    support_tier: "priority",     // Support level
    is_beta_user: true,           // Beta program
    acquisition_channel: "referral"
  },

  // === TRANSACTION CONTEXT ===
  cart: {
    id: "cart_789",
    item_count: 5,
    unique_products: 3,
    total_cents: 45999,
    currency: "USD",
    has_subscription_items: true,
    coupon_code: "SAVE20",
    discount_cents: 9200
  },

  // === BUSINESS OPERATION ===
  checkout: {
    flow_type: "express",         // Which checkout variant
    payment_method: "saved_card",
    shipping_method: "express",
    is_gift: false,
    requires_signature: true
  },

  // === FEATURE CONTEXT ===
  experiment: {
    checkout_variant: "new_v2",   // A/B test bucket
    recommendation_model: "ml_v3",
    pricing_tier: "dynamic"
  }
};
```

### Good Example: SaaS/API Context

```javascript
const event = {
  // ... required fields ...

  // === CUSTOMER CONTEXT ===
  customer: {
    id: "cust_abc123",
    plan: "enterprise",
    mrr_cents: 299900,            // Monthly revenue
    seats_used: 45,
    seats_limit: 50,
    contract_end_date: "2025-12-31",
    is_churning_risk: false,
    customer_success_tier: "high_touch"
  },

  // === API USAGE ===
  api: {
    endpoint: "/v2/documents/analyze",
    api_version: "2024-01",
    quota_remaining: 8547,
    quota_limit: 10000,
    is_rate_limited: false
  },

  // === RESOURCE CONTEXT ===
  resource: {
    type: "document",
    id: "doc_xyz789",
    size_bytes: 1024000,
    page_count: 47,
    owner_id: "user_456"
  },

  // === BILLING IMPACT ===
  billing: {
    metered_units: 47,            // Usage-based billing
    estimated_cost_cents: 235,
    is_overage: false
  }
};
```

### Domain-Specific Queries Enabled

```sql
-- "Which enterprise customers are hitting rate limits?"
SELECT customer.id, customer.plan, COUNT(*) as limit_hits
FROM logs
WHERE api.is_rate_limited = true
  AND customer.plan = 'enterprise'
  AND timestamp > NOW() - INTERVAL 24 HOUR
GROUP BY customer.id, customer.plan;

-- "Revenue impact of checkout failures by experiment variant"
SELECT
  experiment.checkout_variant,
  COUNT(*) as failures,
  SUM(cart.total_cents) / 100 as lost_revenue_dollars
FROM logs
WHERE outcome = 'failure'
  AND path = '/checkout'
GROUP BY experiment.checkout_variant;

-- "API errors for customers nearing quota"
SELECT customer.id, error.code, api.quota_remaining
FROM logs
WHERE outcome = 'failure'
  AND api.quota_remaining < 100
  AND customer.mrr_cents > 100000;
```

### Bad Example: No Business Context

```javascript
// ❌ Pure technical—can't answer business questions
const event = {
  request_id: "abc123",
  method: "POST",
  path: "/checkout",
  status: 500,
  duration_ms: 234
};

// "Are enterprise customers affected?" — Can't answer
// "What's the revenue impact?" — Can't answer
// "Which A/B variant is failing?" — Can't answer
```

### Checklist

- [ ] User tier/subscription level included
- [ ] Business entity details (cart total, order value, etc.)
- [ ] Feature flag / experiment bucketing captured
- [ ] Domain-specific metadata present
- [ ] Revenue-relevant fields included
- [ ] Can answer "which customers are affected?" from logs alone
