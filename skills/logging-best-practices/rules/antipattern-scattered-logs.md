---
title: Anti-Pattern - Scattered Log Statements
impact: CRITICAL
tags: anti-pattern, debugging, wide-events
---

## Anti-Pattern: Scattered Log Statements

**Impact: CRITICAL**

Scattered `console.log` or `logger.info` statements throughout code create debugging nightmares at scale. Replace with the wide events pattern.

### The Problem

```javascript
// ❌ SCATTERED LOGGING ANTI-PATTERN
async function processCheckout(req, res) {
  console.log('Checkout started');                    // No context

  const user = await getUser(req.userId);
  console.log(`User found: ${user.id}`);              // Different format

  const cart = await getCart(req.cartId);
  logger.info('Cart retrieved', { cartId: cart.id }); // Yet another format

  console.log(`Cart total: ${cart.total}`);

  try {
    const payment = await processPayment(cart, user);
    console.log('Payment successful');
    logger.info('Order created', { orderId: payment.orderId });
  } catch (error) {
    console.error('Payment failed:', error.message);  // Lost context
    throw error;
  }

  console.log('Checkout completed');
}
```

### Why This Fails at Scale

| Problem | Impact |
|---------|--------|
| **No correlation** | Can't link logs from same request |
| **Inconsistent format** | Some structured, some strings |
| **Lost context** | Error log doesn't include user/cart details |
| **Noise** | 8 log lines per request × 10K RPS = 80K logs/second |
| **Grep archaeology** | Finding related logs requires multiple searches |

### The Solution: One Wide Event

```javascript
// ✅ WIDE EVENT PATTERN
async function processCheckout(req, res) {
  const event = {
    request_id: req.id,
    timestamp: Date.now(),
    service: 'checkout',
    path: '/checkout',
    method: 'POST'
  };

  try {
    const user = await getUser(req.userId);
    event.user = {
      id: user.id,
      tier: user.tier,
      account_age_days: user.accountAgeDays
    };

    const cart = await getCart(req.cartId);
    event.cart = {
      id: cart.id,
      item_count: cart.items.length,
      total_cents: cart.total
    };

    const paymentStart = Date.now();
    const payment = await processPayment(cart, user);
    event.payment = {
      provider: payment.provider,
      latency_ms: Date.now() - paymentStart,
      order_id: payment.orderId
    };

    event.outcome = 'success';
    event.duration_ms = Date.now() - event.timestamp;

  } catch (error) {
    event.outcome = 'failure';
    event.error = {
      type: error.name,
      code: error.code,
      message: error.message
    };
    event.duration_ms = Date.now() - event.timestamp;
    throw error;

  } finally {
    // ONE log per request, with FULL context
    logger.info(event);
  }
}
```

### Comparison

| Scattered | Wide Event |
|-----------|------------|
| 8 log statements | 1 log statement |
| No correlation ID | request_id links everything |
| Mixed formats | Consistent structure |
| Error loses context | Error includes full request context |
| 80K logs/second | 10K logs/second |
| Multiple grep searches | Single query |

### Detection Checklist

When reviewing code, flag these patterns:

- [ ] Multiple `console.log`/`logger.x` in same function
- [ ] Log statements without request/correlation ID
- [ ] String interpolation in logs: `logger.info(\`User ${id}\`)`
- [ ] `console.log('starting...')` / `console.log('done')`
- [ ] Error logs that don't include request context
- [ ] Mixed `console` and structured logger usage

### Refactoring Steps

1. Identify all log statements in the function
2. Create single event object at function start
3. Replace each log with event enrichment
4. Move emit to `finally` block (or completion middleware)
5. Include error context in catch blocks
6. Delete all intermediate log statements
