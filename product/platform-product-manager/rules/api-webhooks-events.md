---
title: Webhooks and Event-Driven APIs
impact: HIGH
tags: webhooks, events, async, real-time, notifications
---

## Webhooks and Event-Driven APIs

**Impact: HIGH**

Webhooks turn your API from request-response into a real-time platform. They're how developers build reactive integrations.

### Webhook vs Polling Comparison

| Factor | Webhooks | Polling |
|--------|----------|---------|
| **Latency** | Real-time (seconds) | Minutes to hours |
| **Efficiency** | Only when changes occur | Constant requests |
| **Complexity** | Endpoint setup required | Simple GET requests |
| **Reliability** | Needs retry logic | Simpler recovery |
| **Cost** | Lower for provider | Higher API usage |

### Event Naming Conventions

**Good event naming:**

```
{resource}.{action}

customer.created
customer.updated
customer.deleted

order.placed
order.fulfilled
order.cancelled

payment.succeeded
payment.failed
payment.refunded

subscription.created
subscription.upgraded
subscription.cancelled
```

**Event naming rules:**
- Use resource.action format
- Past tense for completed actions
- Lowercase, dot-separated
- Be specific (not generic `data.changed`)

### Webhook Payload Structure

**Complete webhook payload:**

```json
{
  "id": "evt_1NqINN2eZvKYlo2C4LsR",
  "object": "event",
  "type": "customer.created",
  "created": 1705312200,
  "api_version": "2024-01-01",
  "data": {
    "object": {
      "id": "cus_NqINNKdSBqHhzG",
      "object": "customer",
      "email": "customer@example.com",
      "name": "Jane Doe",
      "created": 1705312200
    },
    "previous_attributes": null
  },
  "request": {
    "id": "req_abc123",
    "idempotency_key": "key_xyz789"
  },
  "livemode": true
}
```

**Essential payload fields:**

| Field | Purpose |
|-------|---------|
| **id** | Unique event identifier |
| **type** | Event type (resource.action) |
| **created** | Unix timestamp of event |
| **api_version** | API version that generated event |
| **data.object** | Full resource state after change |
| **data.previous_attributes** | Changed fields (for updates) |
| **livemode** | Production vs test |

### Webhook Delivery Guarantees

**Delivery semantics:**

| Guarantee | Description | Implementation |
|-----------|-------------|----------------|
| **At-least-once** | Events may be delivered multiple times | Standard - require idempotent handling |
| **At-most-once** | Events delivered once or not at all | Not recommended |
| **Exactly-once** | Events delivered exactly once | Very hard - use at-least-once + idempotency |

### Retry Strategy

**Exponential backoff schedule:**

| Attempt | Delay | Cumulative |
|---------|-------|------------|
| 1 | Immediate | 0s |
| 2 | 30s | 30s |
| 3 | 5m | 5.5m |
| 4 | 30m | 35.5m |
| 5 | 2h | 2h 35.5m |
| 6 | 5h | 7h 35.5m |
| 7 | 10h | 17h 35.5m |
| 8 | 24h | 41h 35.5m |

**After max retries:**
- Mark webhook as failed
- Email notification to developer
- Available in dashboard for manual retry

### Webhook Signature Verification

**Signature header format:**

```http
POST /webhook HTTP/1.1
Content-Type: application/json
X-Signature: t=1705312200,v1=5257a869e...
X-Webhook-ID: wh_1NqINN2eZvKYlo2C

{webhook payload}
```

**Verification steps:**

```python
import hmac
import hashlib
import time

def verify_signature(payload, header, secret):
    # Parse signature header
    parts = dict(p.split('=') for p in header.split(','))
    timestamp = int(parts['t'])
    signature = parts['v1']

    # Check timestamp (prevent replay)
    if abs(time.time() - timestamp) > 300:  # 5 min tolerance
        return False

    # Compute expected signature
    signed_payload = f"{timestamp}.{payload}"
    expected = hmac.new(
        secret.encode(),
        signed_payload.encode(),
        hashlib.sha256
    ).hexdigest()

    # Compare (timing-safe)
    return hmac.compare_digest(expected, signature)
```

### Webhook Endpoint Configuration

**Configuration options to provide:**

| Option | Description | Example |
|--------|-------------|---------|
| **URL** | Endpoint to receive webhooks | https://example.com/webhook |
| **Events** | Which events to receive | `customer.*`, `payment.succeeded` |
| **Secret** | Signing secret | `whsec_abc123...` |
| **API version** | Payload format version | `2024-01-01` |
| **Enabled** | Active/inactive toggle | true |

### Webhook Dashboard Features

**Essential dashboard views:**

```
Webhooks
├── Endpoints
│   ├── Create endpoint
│   ├── Edit endpoint
│   └── Delete endpoint
│
├── Event logs
│   ├── Filter by event type
│   ├── Filter by status
│   ├── View payload
│   └── Manual retry
│
├── Testing
│   ├── Send test event
│   └── Local testing setup
│
└── Metrics
    ├── Delivery rate
    ├── Average latency
    └── Failure reasons
```

### Handling Webhook Best Practices

**Good webhook handler:**

```python
@app.route('/webhook', methods=['POST'])
def handle_webhook():
    payload = request.get_data(as_text=True)
    sig_header = request.headers.get('X-Signature')

    # 1. Verify signature
    if not verify_signature(payload, sig_header, webhook_secret):
        return 'Invalid signature', 400

    event = json.loads(payload)

    # 2. Check idempotency (already processed?)
    if already_processed(event['id']):
        return 'OK', 200

    # 3. Route to handler
    try:
        if event['type'] == 'customer.created':
            handle_customer_created(event['data']['object'])
        elif event['type'] == 'payment.succeeded':
            handle_payment_succeeded(event['data']['object'])
        # ... more handlers

        # 4. Mark as processed
        mark_processed(event['id'])

    except Exception as e:
        # Log but return 200 to prevent retries for app errors
        log_error(e, event)

    return 'OK', 200
```

**Handler rules:**
1. Respond quickly (< 30 seconds)
2. Process asynchronously for heavy work
3. Be idempotent
4. Return 2xx for success
5. Return 4xx/5xx only for issues you want retried

### Event Ordering

**Events may arrive out of order:**

```
Actual order:       Delivery order (possible):
1. order.created    1. order.created
2. order.updated    2. order.fulfilled
3. order.fulfilled  3. order.updated
```

**Handling out-of-order events:**
- Use `created` timestamp for ordering
- Include version/sequence numbers
- Design handlers to be order-independent
- Use `data.previous_attributes` for state comparison

### Testing Webhooks

**Local development options:**

| Tool | Description |
|------|-------------|
| **CLI forwarding** | `example listen --forward localhost:3000/webhook` |
| **ngrok** | Expose local server to internet |
| **Dashboard testing** | Send test events from dashboard |
| **Mock endpoints** | Webhook.site, RequestBin |

**Test event payload:**

```json
{
  "id": "evt_test_123",
  "type": "customer.created",
  "data": {
    "object": {
      "id": "cus_test_123",
      "email": "test@example.com"
    }
  },
  "livemode": false
}
```

### Event Documentation

**Document each event type:**

```markdown
# customer.created

Occurs when a new customer is created.

## Payload

```json
{
  "type": "customer.created",
  "data": {
    "object": {
      "id": "cus_123",
      "email": "customer@example.com",
      "name": "Jane Doe",
      "created": 1705312200
    }
  }
}
```

## Triggers
- API: `POST /v1/customers`
- Dashboard: Creating customer
- Checkout: New customer during checkout

## Related events
- `customer.updated`
- `customer.deleted`
```

### Anti-Patterns

- **No signature verification** — Anyone can spoof webhooks
- **Synchronous processing** — Slow handlers cause timeouts
- **No idempotency** — Duplicate events cause duplicate actions
- **Returning errors for app bugs** — Causes infinite retries
- **No event logs** — Can't debug delivery issues
- **Missing events** — Not exposing important state changes
- **No test mode** — Hard to develop against
- **No manual retry** — Can't recover from failures
- **Undocumented events** — Developers don't know what to expect
- **Breaking payload changes** — Changing event structure without versioning
