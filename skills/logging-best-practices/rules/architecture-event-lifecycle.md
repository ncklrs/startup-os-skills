---
title: Event Lifecycle Management
impact: HIGH
tags: architecture, lifecycle, context-propagation
---

## Event Lifecycle Management

**Impact: HIGH**

Build your wide event progressively through the request lifecycle, enriching with context at each stage, then emit once at completion.

### Pattern: Request Context Builder

```typescript
// middleware/requestContext.ts
import { AsyncLocalStorage } from 'async_hooks';

interface RequestEvent {
  request_id: string;
  timestamp: number;
  service: string;
  version: string;
  method: string;
  path: string;
  user?: UserContext;
  business?: Record<string, unknown>;
  metrics?: Record<string, number>;
  error?: ErrorContext;
  outcome?: 'success' | 'failure';
  duration_ms?: number;
}

const eventStorage = new AsyncLocalStorage<RequestEvent>();

// Initialize at request start
export function initRequestEvent(req: Request): void {
  const event: RequestEvent = {
    request_id: req.id ?? crypto.randomUUID(),
    timestamp: Date.now(),
    service: process.env.SERVICE_NAME!,
    version: process.env.SERVICE_VERSION!,
    method: req.method,
    path: req.path,
  };
  eventStorage.enterWith(event);
}

// Enrich throughout request
export function enrichEvent(data: Partial<RequestEvent>): void {
  const event = eventStorage.getStore();
  if (event) {
    Object.assign(event, data);
  }
}

// Add nested context
export function addUserContext(user: UserContext): void {
  enrichEvent({ user });
}

export function addBusinessContext(key: string, value: unknown): void {
  const event = eventStorage.getStore();
  if (event) {
    event.business = { ...event.business, [key]: value };
  }
}

export function recordMetric(key: string, value: number): void {
  const event = eventStorage.getStore();
  if (event) {
    event.metrics = { ...event.metrics, [key]: value };
  }
}

// Emit at request end
export function finalizeEvent(outcome: 'success' | 'failure'): RequestEvent {
  const event = eventStorage.getStore()!;
  event.outcome = outcome;
  event.duration_ms = Date.now() - event.timestamp;
  return event;
}
```

### Good Example: Express Middleware

```typescript
// Middleware chain that builds event progressively

app.use((req, res, next) => {
  initRequestEvent(req);
  next();
});

app.use(authMiddleware); // Adds user context

app.post('/checkout', async (req, res) => {
  const startDb = Date.now();
  const cart = await getCart(req.body.cartId);
  recordMetric('db_latency_ms', Date.now() - startDb);

  addBusinessContext('cart', {
    id: cart.id,
    item_count: cart.items.length,
    total_cents: cart.total
  });

  const startPayment = Date.now();
  const result = await processPayment(cart);
  recordMetric('payment_latency_ms', Date.now() - startPayment);

  addBusinessContext('payment', {
    method: result.method,
    provider: result.provider
  });

  res.json({ orderId: result.orderId });
});

// Final middleware emits event
app.use((req, res, next) => {
  res.on('finish', () => {
    const outcome = res.statusCode < 400 ? 'success' : 'failure';
    const event = finalizeEvent(outcome);
    event.status_code = res.statusCode;
    logger.info(event);
  });
  next();
});
```

### Bad Example: Context Lost Across Boundaries

```javascript
// ❌ Context doesn't flow through async boundaries
app.post('/checkout', async (req, res) => {
  console.log('checkout started'); // No context

  await someAsyncOperation(); // Context lost

  console.log('payment done'); // Still no context
});
```

### Framework Patterns

| Framework | Context Propagation |
|-----------|---------------------|
| Node.js | `AsyncLocalStorage` |
| Python | `contextvars` |
| Go | `context.Context` |
| Java | `ThreadLocal` / MDC |
| .NET | `AsyncLocal<T>` |

### Checklist

- [ ] Initialize event at request entry point
- [ ] Use framework-appropriate context propagation
- [ ] Enrich at each significant stage (auth, business logic, external calls)
- [ ] Record timing metrics for each operation
- [ ] Capture errors with full context before emitting
- [ ] Emit exactly once at request completion
