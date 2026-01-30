---
title: Embrace High-Cardinality Fields
impact: CRITICAL
tags: fields, cardinality, debugging
---

## Embrace High-Cardinality Fields

**Impact: CRITICAL**

High-cardinality fields (user IDs, order IDs, session IDs) are where real debugging power lies. Traditional observability treated these as expensive or problematic—modern columnar databases handle them efficiently.

### Understanding Cardinality

| Cardinality | Examples | Debugging Value |
|-------------|----------|-----------------|
| **Low** | HTTP methods, status codes, regions | Limited—everyone has these |
| **Medium** | Endpoints, error types, features | Useful for aggregation |
| **High** | User IDs, order IDs, trace IDs | **Maximum**—enables precise debugging |

### The Misconception

> "High-cardinality data is expensive and should be avoided"

**Reality:** Modern columnar databases (ClickHouse, BigQuery, Snowflake) are designed for high-cardinality queries. The cost of NOT having this data is hours of debugging.

### Good Example: Rich High-Cardinality Context

```javascript
const event = {
  // High-cardinality identifiers (THE GOOD STUFF)
  request_id: "req_7f3b2a1c",
  trace_id: "trace_abc123def456",
  user_id: "user_12345",
  account_id: "acc_98765",
  session_id: "sess_xyz789",
  order_id: "ord_555666",
  cart_id: "cart_111222",

  // Also high-cardinality but often missed
  correlation_id: "corr_parent_request",
  idempotency_key: "idem_client_generated",

  // User attributes (enable cohort analysis)
  user: {
    id: "user_12345",
    email_domain: "company.com", // Not full email—privacy
    signup_date: "2023-06-15",
    subscription_tier: "enterprise",
    lifetime_orders: 47,
    lifetime_value_cents: 234500
  },

  // Transaction details
  transaction: {
    id: "txn_789",
    amount_cents: 15999,
    currency: "USD",
    payment_method_id: "pm_card_visa_1234"
  }
};
```

### Bad Example: Only Low-Cardinality Data

```javascript
// ❌ Useless for debugging specific issues
const event = {
  method: "POST",
  path: "/checkout",
  status: 500,
  service: "checkout",
  region: "us-east-1"
};

// "500 errors are up in checkout" - but WHICH users? WHICH orders?
```

### Query Power Unlocked

```sql
-- With high-cardinality: "What happened to this specific user?"
SELECT * FROM logs
WHERE user_id = 'user_12345'
ORDER BY timestamp DESC
LIMIT 100;

-- "All requests in this user's session"
SELECT * FROM logs
WHERE session_id = 'sess_xyz789'
ORDER BY timestamp;

-- "Trace this order across all services"
SELECT service, outcome, duration_ms, error.message
FROM logs
WHERE order_id = 'ord_555666'
ORDER BY timestamp;

-- "Which users are hitting this error?"
SELECT user_id, COUNT(*) as occurrences
FROM logs
WHERE error.code = 'PAYMENT_DECLINED'
  AND timestamp > NOW() - INTERVAL 1 HOUR
GROUP BY user_id
ORDER BY occurrences DESC;
```

### High-Cardinality Fields to Always Include

| Field | Why |
|-------|-----|
| `request_id` | Correlate all logs for one request |
| `trace_id` | Cross-service tracing |
| `user_id` | Debug user-specific issues |
| `account_id` | Multi-tenant isolation |
| `session_id` | User journey analysis |
| `order_id` / `transaction_id` | Business operation tracking |
| `correlation_id` | Parent-child request chains |

### Checklist

- [ ] Include all relevant entity IDs (user, account, order, session)
- [ ] Add trace/correlation IDs for distributed tracing
- [ ] Include business entity IDs (cart, invoice, subscription)
- [ ] Don't avoid high-cardinality—embrace it
- [ ] Use columnar database designed for high-cardinality queries
