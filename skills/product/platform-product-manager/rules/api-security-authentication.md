---
title: API Security and Authentication
impact: CRITICAL
tags: security, authentication, authorization, api-keys, oauth
---

## API Security and Authentication

**Impact: CRITICAL**

Security is non-negotiable for APIs. One breach destroys developer trust permanently.

### Authentication Methods Comparison

| Method | Security | UX | Best For |
|--------|----------|-----|----------|
| **API Keys** | Medium | Simple | Server-to-server |
| **OAuth 2.0** | High | Complex | User authorization |
| **JWT** | Medium-High | Medium | Stateless auth |
| **mTLS** | Very High | Complex | Enterprise, high-security |
| **Basic Auth** | Low | Simple | Legacy, internal only |

### API Key Design

**Good API key format:**

```
{prefix}_live_{random_string}   (secret key, production)
{prefix}_test_{random_string}   (secret key, test)
pk_live_{random_string}         (publishable key, production)
pk_test_{random_string}         (publishable key, test)

Example: acme_live_a1b2c3d4e5f6g7h8i9j0
```

**Key components:**
- **Prefix**: Type identifier (`sk_`, `pk_`)
- **Environment**: `live` or `test`
- **Random string**: High entropy, 24-32 characters

**API key management:**

| Feature | Priority | Purpose |
|---------|----------|---------|
| **Key rotation** | Critical | Change keys without downtime |
| **Multiple keys** | Critical | Different keys for different purposes |
| **Key restrictions** | High | IP, domain, scope limits |
| **Usage tracking** | High | Audit, billing |
| **Expiration** | Medium | Time-limited access |
| **Labels** | Medium | Identify key purpose |

### OAuth 2.0 Implementation

**Common OAuth flows:**

| Flow | Use Case | Security Level |
|------|----------|----------------|
| **Authorization Code + PKCE** | Web apps, mobile | Highest |
| **Client Credentials** | Server-to-server | High |
| **Device Code** | CLIs, TVs | Medium |
| **Implicit** (deprecated) | Legacy SPAs | Low - Avoid |

**Authorization code flow:**

```
┌──────────┐                              ┌──────────┐
│  Client  │                              │  Auth    │
│  App     │                              │  Server  │
└────┬─────┘                              └────┬─────┘
     │                                          │
     │ 1. Redirect to /authorize                │
     │ ────────────────────────────────────────►│
     │                                          │
     │ 2. User authenticates                    │
     │                                          │
     │ 3. Redirect with authorization code      │
     │ ◄────────────────────────────────────────│
     │                                          │
     │ 4. Exchange code for token               │
     │ ────────────────────────────────────────►│
     │                                          │
     │ 5. Return access + refresh tokens        │
     │ ◄────────────────────────────────────────│
     │                                          │
```

### Token Best Practices

**Access token design:**

| Property | Recommendation |
|----------|----------------|
| **Format** | JWT or opaque |
| **Lifetime** | 15 min - 1 hour |
| **Storage** | Memory only (client) |
| **Revocation** | Supported via blocklist |
| **Scope** | Minimal required permissions |

**Refresh token design:**

| Property | Recommendation |
|----------|----------------|
| **Lifetime** | 7-30 days |
| **Rotation** | New refresh token on use |
| **Storage** | Secure, encrypted |
| **Revocation** | Immediate on logout |

### Scopes and Permissions

**Good scope design:**

```
read:users          # Read user data
write:users         # Create/update users
delete:users        # Delete users

read:orders         # Read orders
write:orders        # Create orders
admin:orders        # Full order access

read:*              # Read all resources
admin:*             # Full access
```

**Scope hierarchy:**

```
admin:users
    │
    ├── write:users
    │       │
    │       └── read:users
    │
    └── delete:users
```

### Rate Limiting Security

**Rate limit by:**

| Dimension | Purpose | Example |
|-----------|---------|---------|
| **API key** | Prevent abuse per customer | 1000 req/min |
| **IP address** | Prevent distributed attacks | 100 req/min |
| **Endpoint** | Protect expensive operations | 10 req/min for /search |
| **User** | Fair usage per user | 100 req/min |

**Rate limit headers:**

```http
HTTP/1.1 200 OK
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 999
X-RateLimit-Reset: 1640995200

HTTP/1.1 429 Too Many Requests
Retry-After: 60
```

### Webhook Security

**Webhook signature verification:**

```python
import hmac
import hashlib

def verify_webhook(payload, signature, secret):
    expected = hmac.new(
        secret.encode(),
        payload.encode(),
        hashlib.sha256
    ).hexdigest()

    return hmac.compare_digest(f"sha256={expected}", signature)

# Usage
is_valid = verify_webhook(
    payload=request.body,
    signature=request.headers['X-Signature'],
    secret=webhook_secret
)
```

**Webhook security checklist:**

- [ ] HMAC signature on all webhooks
- [ ] Timestamp validation (prevent replay)
- [ ] HTTPS endpoints only
- [ ] Retry with exponential backoff
- [ ] Idempotency support
- [ ] IP allowlist option

### Security Headers

**Required response headers:**

```http
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
Content-Security-Policy: default-src 'none'
Cache-Control: no-store
```

### Input Validation

**Validate all inputs:**

| Input Type | Validation |
|------------|------------|
| **Strings** | Max length, character set, sanitization |
| **Numbers** | Min/max range, type |
| **Emails** | Format, domain validation |
| **URLs** | Protocol whitelist, format |
| **IDs** | Format, existence |
| **Arrays** | Max length, item validation |
| **Objects** | Schema validation |

**Validation error response:**

```json
{
  "error": {
    "code": "validation_error",
    "message": "Request validation failed",
    "details": [
      {
        "field": "email",
        "code": "invalid_format",
        "message": "Must be a valid email address"
      }
    ]
  }
}
```

### Sensitive Data Handling

**Never expose in responses:**
- Full credit card numbers
- Passwords or password hashes
- API secret keys
- Internal IDs that leak information
- PII unless explicitly requested

**Masking patterns:**

```json
{
  "card": {
    "last4": "4242",
    "brand": "visa",
    "exp_month": 12,
    "exp_year": 2025
  }
}
```

### Security Logging

**Log for security:**

| Event | Log Level | Retention |
|-------|-----------|-----------|
| **Authentication failure** | Warn | 90 days |
| **Authorization failure** | Warn | 90 days |
| **Rate limit exceeded** | Info | 30 days |
| **Suspicious patterns** | Warn | 180 days |
| **Admin actions** | Info | 1 year |
| **Data access** | Debug | 30 days |

### Anti-Patterns

- **API keys in URLs** — Query params logged, cached, exposed
- **No rate limiting** — DoS vulnerability
- **Long-lived tokens** — Extended breach window
- **Secrets in responses** — Exposing keys in API responses
- **HTTP allowed** — No HTTPS enforcement
- **No key rotation** — Can't respond to compromises
- **Hardcoded secrets** — Keys in code/configs
- **Overly broad scopes** — All-or-nothing permissions
- **Missing audit logs** — Can't investigate incidents
- **Trust client input** — No server-side validation
