---
title: Developer-Friendly Error Handling
impact: HIGH
tags: dx, errors, debugging, developer-experience
---

## Developer-Friendly Error Handling

**Impact: HIGH**

Errors are inevitable. Great error handling turns frustration into quick fixes. Bad error handling drives developers to competitors.

### Error Response Anatomy

**Complete error response:**

```json
{
  "error": {
    "type": "invalid_request_error",
    "code": "parameter_invalid",
    "message": "The amount must be a positive integer representing cents",
    "param": "amount",
    "doc_url": "https://docs.example.com/api/errors#parameter_invalid",
    "request_id": "req_7d82fcb9e3a4"
  }
}
```

**Essential error fields:**

| Field | Purpose | Required |
|-------|---------|----------|
| **type** | Error category | Yes |
| **code** | Specific error code | Yes |
| **message** | Human-readable explanation | Yes |
| **param** | Which parameter caused error | When applicable |
| **doc_url** | Link to documentation | Recommended |
| **request_id** | For support/debugging | Yes |

### HTTP Status Code Usage

| Code | Name | When to Use |
|------|------|-------------|
| **400** | Bad Request | Invalid syntax, malformed request |
| **401** | Unauthorized | Missing or invalid authentication |
| **403** | Forbidden | Valid auth but insufficient permissions |
| **404** | Not Found | Resource doesn't exist |
| **409** | Conflict | Resource state conflict (duplicate, etc.) |
| **422** | Unprocessable Entity | Validation failed on valid syntax |
| **429** | Too Many Requests | Rate limit exceeded |
| **500** | Internal Server Error | Server-side failure |
| **502** | Bad Gateway | Upstream service failure |
| **503** | Service Unavailable | Maintenance or overload |

### Error Type Categories

```
error.type
├── api_error                 # Server-side issues
│   ├── internal_error
│   ├── service_unavailable
│   └── upstream_error
│
├── authentication_error      # Auth issues
│   ├── invalid_api_key
│   ├── expired_token
│   └── missing_auth
│
├── authorization_error       # Permission issues
│   ├── insufficient_permissions
│   └── restricted_resource
│
├── invalid_request_error     # Client mistakes
│   ├── parameter_missing
│   ├── parameter_invalid
│   └── parameter_unknown
│
├── rate_limit_error          # Rate limiting
│   └── too_many_requests
│
└── resource_error            # Resource issues
    ├── resource_not_found
    ├── resource_already_exists
    └── resource_locked
```

### Validation Error Details

**Good validation error (multiple fields):**

```json
{
  "error": {
    "type": "invalid_request_error",
    "code": "validation_failed",
    "message": "The request contains invalid parameters",
    "details": [
      {
        "field": "email",
        "code": "invalid_format",
        "message": "Email must be a valid email address"
      },
      {
        "field": "amount",
        "code": "out_of_range",
        "message": "Amount must be between 100 and 10000000 (in cents)"
      },
      {
        "field": "metadata.key",
        "code": "invalid_characters",
        "message": "Metadata keys can only contain letters, numbers, and underscores"
      }
    ],
    "request_id": "req_abc123"
  }
}
```

### Error Message Writing Guide

**Good error messages:**

| Bad | Good |
|-----|------|
| "Invalid input" | "The email address format is invalid. Expected: user@domain.com" |
| "Error 1234" | "Your API key has expired. Generate a new key at dashboard.example.com/keys" |
| "Something went wrong" | "The payment processor is temporarily unavailable. Retry in 30 seconds." |
| "null" | "The 'customer_id' field is required" |
| "Unauthorized" | "The API key provided does not have permission to access this resource" |

**Message components:**
1. **What happened** — Clear description of the problem
2. **Why it happened** — Context if helpful
3. **How to fix it** — Actionable next steps

### Idempotent Error Handling

**Same request should return same error:**

```
Request 1:
POST /v1/charges
{ "amount": -100 }

Response 1:
HTTP 422
{ "error": { "code": "invalid_amount", "message": "Amount must be positive" } }

Request 2 (identical):
POST /v1/charges
{ "amount": -100 }

Response 2 (identical):
HTTP 422
{ "error": { "code": "invalid_amount", "message": "Amount must be positive" } }
```

### Retry-After Headers

**For rate limits and temporary errors:**

```http
HTTP/1.1 429 Too Many Requests
Retry-After: 60
X-RateLimit-Limit: 100
X-RateLimit-Remaining: 0
X-RateLimit-Reset: 1640995200

{
  "error": {
    "type": "rate_limit_error",
    "code": "too_many_requests",
    "message": "Rate limit exceeded. Retry after 60 seconds.",
    "retry_after": 60
  }
}
```

**For maintenance:**

```http
HTTP/1.1 503 Service Unavailable
Retry-After: 300

{
  "error": {
    "type": "api_error",
    "code": "service_unavailable",
    "message": "The API is undergoing maintenance. Expected back at 2024-01-15T10:00:00Z",
    "maintenance_expected_end": "2024-01-15T10:00:00Z"
  }
}
```

### SDK Error Handling

**Good SDK error design:**

```python
from example import Client
from example.errors import (
    AuthenticationError,
    RateLimitError,
    ValidationError,
    APIError
)

client = Client("sk_test_...")

try:
    charge = client.charges.create(amount=1000)
except AuthenticationError as e:
    # API key issue
    print(f"Check your API key: {e.message}")
except RateLimitError as e:
    # Wait and retry
    time.sleep(e.retry_after)
    retry()
except ValidationError as e:
    # Fix the request
    for detail in e.details:
        print(f"{detail.field}: {detail.message}")
except APIError as e:
    # Server error - log and alert
    print(f"API error: {e.message}")
    print(f"Request ID: {e.request_id}")
    alert_team(e)
```

### Error Logging for Debugging

**What to include in error logs:**

```json
{
  "timestamp": "2024-01-15T10:30:00Z",
  "request_id": "req_abc123",
  "error_code": "validation_failed",
  "path": "/v1/charges",
  "method": "POST",
  "client_ip": "203.0.113.50",
  "api_version": "2024-01-01",
  "params_sanitized": {
    "amount": 1000,
    "currency": "usd"
  },
  "error_details": [...],
  "stack_trace": "..." // Internal only
}
```

### Deprecation Warnings

**Include warnings for deprecated features:**

```json
{
  "data": { ... },
  "warnings": [
    {
      "code": "deprecated_parameter",
      "message": "The 'source' parameter is deprecated. Use 'payment_method' instead.",
      "deprecated_at": "2024-01-01",
      "removal_date": "2024-07-01",
      "doc_url": "https://docs.example.com/migration/payment-methods"
    }
  ]
}
```

### Error Documentation

**Document every error code:**

```markdown
# API Errors Reference

## authentication_error

### invalid_api_key
Your API key is invalid or has been revoked.

**Causes:**
- Typo in API key
- Using test key in production (or vice versa)
- Key has been deleted

**Solutions:**
1. Verify your key at Dashboard → API Keys
2. Ensure you're using the correct environment key
3. Generate a new key if needed

**Example:**
```json
{
  "error": {
    "type": "authentication_error",
    "code": "invalid_api_key",
    "message": "The API key provided is invalid"
  }
}
```
```

### Anti-Patterns

- **Generic errors** — "Something went wrong" tells developers nothing
- **Missing request IDs** — Can't trace errors through support
- **Wrong status codes** — Using 200 for errors, 500 for validation
- **No error codes** — Only human messages, can't programmatically handle
- **Exposing internals** — Stack traces, database errors in production
- **Inconsistent format** — Different error shapes for different endpoints
- **No retry guidance** — Rate limits without Retry-After
- **Undocumented errors** — Error codes not in documentation
- **Leaking information** — "User not found" vs "Invalid credentials"
- **Silent failures** — Succeeding when it should error
