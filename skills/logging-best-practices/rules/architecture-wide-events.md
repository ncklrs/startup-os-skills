---
title: Wide Events Architecture
impact: CRITICAL
tags: architecture, wide-events, canonical-log-line
---

## Wide Events Architecture

**Impact: CRITICAL**

Emit **one comprehensive event per request per service** instead of scattered log statements. This is the canonical log line pattern—consolidating all debugging information into a single queryable record.

### Why This Matters

Traditional scattered logging creates:
- Signal-to-noise problems at scale
- Inconsistent field naming across statements
- Impossible cross-request correlation
- String-search archaeology instead of analytics

Wide events transform logging from archaeology → analytics.

### Good Example

```javascript
// Build event throughout request lifecycle
const event = {
  // Request metadata
  request_id: req.id,
  trace_id: req.headers['x-trace-id'],
  timestamp: Date.now(),

  // Service context
  service: "checkout",
  version: "2.3.1",
  region: "us-east-1",
  instance_id: process.env.INSTANCE_ID,

  // User context
  user: {
    id: userId,
    tier: "premium",
    account_age_days: 847,
    lifetime_value_cents: 2340000
  },

  // Business context
  cart: {
    id: cartId,
    item_count: 3,
    total_cents: 15999,
    coupon_applied: "SAVE20"
  },

  // Operation metrics
  payment: {
    method: "card",
    provider: "stripe",
    latency_ms: 234,
    attempt: 1
  },

  // Outcome
  outcome: "success",
  duration_ms: 487,

  // Feature flags active
  feature_flags: ["new_checkout_v2", "express_payment"]
};

// Emit ONCE at request completion
logger.info(event);
```

### Bad Example

```javascript
// ❌ Scattered logging - debugging nightmare at scale
logger.info("Request started");
logger.debug(`Processing user ${userId}`);
logger.info("User authenticated successfully");
logger.debug(`Found cart with ${items.length} items`);
logger.info("Initiating payment");
logger.debug(`Using provider: stripe`);
logger.info("Payment processed");
logger.info("Order created");
logger.info("Request completed");
```

### Queryable Power

With wide events, answer complex questions in one query:

```sql
-- "Why are premium users failing checkout more than usual?"
SELECT
  error.code,
  COUNT(*) as failures,
  AVG(payment.latency_ms) as avg_latency
FROM logs
WHERE
  service = 'checkout'
  AND outcome = 'failure'
  AND user.tier = 'premium'
  AND timestamp > NOW() - INTERVAL 1 HOUR
GROUP BY error.code
ORDER BY failures DESC
```

### Checklist

- [ ] One event per request per service (not multiple log statements)
- [ ] Build event progressively through request lifecycle
- [ ] Include request, user, business, and technical context
- [ ] Emit at request completion (success or failure)
- [ ] 40+ fields for rich dimensionality
- [ ] Consistent field naming across services
