---
title: Anti-Pattern - OTel as Silver Bullet
impact: MEDIUM-HIGH
tags: anti-pattern, opentelemetry, observability
---

## Anti-Pattern: OpenTelemetry as Silver Bullet

**Impact: MEDIUM-HIGH**

OpenTelemetry is a **delivery protocol**, not a solution architecture. It doesn't determine what to log, add business context, or fix flawed mental models.

### The Misconception

> "We use OpenTelemetry, so observability is solved."

**Reality:** Most OTel implementations capture only span names, duration, and status—insufficient for effective debugging.

### What OTel Is vs. Isn't

| OTel IS | OTel ISN'T |
|---------|------------|
| Standardized data export format | A solution for what to log |
| Vendor-agnostic wire protocol | Automatic business context |
| Trace context propagation | A replacement for wide events |
| SDK for instrumentation | A strategy for observability |

### Minimal OTel Implementation (Common)

```javascript
// ❌ What most teams end up with
// Auto-instrumented, no custom context
const tracer = trace.getTracer('checkout-service');

async function checkout(req, res) {
  const span = tracer.startSpan('checkout');

  try {
    await processPayment();
    span.setStatus({ code: SpanStatusCode.OK });
  } catch (error) {
    span.setStatus({ code: SpanStatusCode.ERROR });
    span.recordException(error);
    throw error;
  } finally {
    span.end();
  }
}

// Result: You know checkout took 500ms and failed
// You DON'T know: which user, what cart value, what payment method,
// which feature flags, what error code, is this a VIP customer...
```

### OTel + Wide Events (Correct)

```javascript
// ✅ OTel for tracing, wide events for context
const tracer = trace.getTracer('checkout-service');

async function checkout(req, res) {
  const span = tracer.startSpan('checkout');

  // Build wide event alongside span
  const event = {
    trace_id: span.spanContext().traceId,
    span_id: span.spanContext().spanId,
    request_id: req.id,
    timestamp: Date.now(),
    service: 'checkout'
  };

  try {
    const user = await getUser(req.userId);
    event.user = { id: user.id, tier: user.tier, ltv_cents: user.ltv };
    span.setAttribute('user.tier', user.tier);

    const cart = await getCart(req.cartId);
    event.cart = { id: cart.id, total_cents: cart.total, item_count: cart.items.length };
    span.setAttribute('cart.total_cents', cart.total);

    const payment = await processPayment(cart, user);
    event.payment = { provider: payment.provider, method: payment.method };

    event.outcome = 'success';
    span.setStatus({ code: SpanStatusCode.OK });

  } catch (error) {
    event.outcome = 'failure';
    event.error = { type: error.name, code: error.code, message: error.message };
    span.setStatus({ code: SpanStatusCode.ERROR });
    span.recordException(error);
    throw error;

  } finally {
    event.duration_ms = Date.now() - event.timestamp;
    span.end();

    // Wide event provides queryable context
    logger.info(event);
  }
}
```

### Complementary, Not Competitive

| Use Case | Best Tool |
|----------|-----------|
| Cross-service request flow | OTel traces |
| Service latency breakdown | OTel spans |
| "What happened in this service?" | Wide events |
| Business context queries | Wide events |
| User-specific debugging | Wide events |
| Performance percentiles | OTel metrics OR wide events |

### OTel Attributes Are Not Wide Events

```javascript
// ❌ Stuffing everything into span attributes
span.setAttribute('user.id', userId);
span.setAttribute('user.tier', tier);
span.setAttribute('cart.total', total);
span.setAttribute('cart.items', itemCount);
// ... 40 more attributes

// Problems:
// - Most trace backends have attribute cardinality limits
// - Query capabilities vary wildly between vendors
// - Not designed for analytics/aggregation
```

### Checklist

- [ ] OTel traces for cross-service flow visualization
- [ ] Wide events for rich, queryable context within services
- [ ] Link wide events to traces via trace_id/span_id
- [ ] Business context in wide events, not just span attributes
- [ ] Don't rely solely on auto-instrumentation
- [ ] Understand your trace backend's query limitations
