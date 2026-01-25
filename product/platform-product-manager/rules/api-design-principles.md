---
title: API Design Principles
impact: CRITICAL
tags: api, design, rest, graphql, standards
---

## API Design Principles

**Impact: CRITICAL**

APIs are user interfaces for developers. Design them with the same rigor and care you'd apply to visual UIs.

### The Five Pillars of API Design

| Pillar | Description | Example |
|--------|-------------|---------|
| **Consistency** | Same patterns everywhere | Always use `created_at` not sometimes `createdAt` |
| **Predictability** | Developers guess correctly | `GET /users/{id}` returns user, not array |
| **Discoverability** | Self-documenting | Clear naming, HATEOAS links |
| **Reliability** | Behaves as expected | Same input = same output |
| **Simplicity** | Easy to understand | Minimal parameters for common cases |

### Resource Naming Conventions

**Good resource naming:**

```
GET    /users                    # List users
GET    /users/{id}               # Get single user
POST   /users                    # Create user
PATCH  /users/{id}               # Update user
DELETE /users/{id}               # Delete user

GET    /users/{id}/orders        # User's orders (nested resource)
GET    /orders/{id}              # Order by ID (top-level access)
```

**Bad resource naming:**

```
GET    /getUsers                 # Verb in URL
GET    /user/{id}                # Inconsistent singular/plural
POST   /users/create             # Redundant action
GET    /users/{id}/getOrders     # Verb in nested resource
GET    /api/v1/Users             # Inconsistent casing
```

### HTTP Methods Matrix

| Method | Idempotent | Safe | Use For |
|--------|------------|------|---------|
| **GET** | Yes | Yes | Reading resources |
| **POST** | No | No | Creating resources, actions |
| **PUT** | Yes | No | Full resource replacement |
| **PATCH** | No* | No | Partial updates |
| **DELETE** | Yes | No | Removing resources |

*PATCH can be idempotent if designed carefully

### Response Envelope Pattern

**Consistent response structure:**

```json
{
  "data": {
    "id": "usr_123",
    "email": "dev@example.com",
    "created_at": "2024-01-15T10:30:00Z"
  },
  "meta": {
    "request_id": "req_abc123"
  }
}
```

**List responses with pagination:**

```json
{
  "data": [
    { "id": "usr_123", "email": "dev1@example.com" },
    { "id": "usr_456", "email": "dev2@example.com" }
  ],
  "meta": {
    "total_count": 150,
    "page": 1,
    "per_page": 20,
    "has_more": true
  },
  "links": {
    "self": "/users?page=1",
    "next": "/users?page=2",
    "last": "/users?page=8"
  }
}
```

### Error Response Design

**Good error responses:**

```json
{
  "error": {
    "code": "validation_error",
    "message": "The request body contains invalid fields",
    "details": [
      {
        "field": "email",
        "code": "invalid_format",
        "message": "Email must be a valid email address"
      },
      {
        "field": "amount",
        "code": "out_of_range",
        "message": "Amount must be between 1 and 10000"
      }
    ],
    "doc_url": "https://docs.example.com/errors/validation_error",
    "request_id": "req_abc123"
  }
}
```

**Bad error responses:**

```json
{
  "error": "Something went wrong"
}

{
  "success": false,
  "message": "Invalid input"
}

{
  "code": 400
}
```

### ID Design Principles

| Approach | Pros | Cons | Best For |
|----------|------|------|----------|
| **Prefixed IDs** (`usr_123`) | Type-safe, debuggable | Slightly longer | External APIs |
| **UUIDs** | Globally unique, no sequence | Long, not human-readable | Distributed systems |
| **Sequential integers** | Short, simple | Guessable, leaks info | Internal systems |
| **Hashids** | Short, non-sequential | Adds dependency | URL shorteners |

**Prefixed ID pattern (recommended):**

```
usr_2cDnPmQTz4         # User
ord_8bKmLpNwQr         # Order
txn_3gHjRsTvWx         # Transaction
api_key_4nLmOpQrSt     # API key
```

### Request Parameter Guidelines

**Query parameters for filtering/options:**

```
GET /users?status=active&created_after=2024-01-01&limit=50
GET /orders?customer_id=cust_123&include=line_items
```

**Path parameters for resource identification:**

```
GET /users/{user_id}/orders/{order_id}
```

**Request body for complex data:**

```json
POST /orders
{
  "customer_id": "cust_123",
  "line_items": [
    { "product_id": "prod_456", "quantity": 2 }
  ]
}
```

### Idempotency Design

**Idempotency key pattern:**

```
POST /charges
Idempotency-Key: abc123-unique-key

{
  "amount": 1000,
  "currency": "usd"
}
```

**Server handling:**
1. Check if idempotency key exists
2. If exists, return cached response
3. If new, process request and cache response

### Field Naming Standards

| Convention | Example | Use Case |
|------------|---------|----------|
| **snake_case** | `created_at` | Most REST APIs (recommended) |
| **camelCase** | `createdAt` | JavaScript-heavy ecosystems |
| **Choose one and be consistent** | | Always |

**Timestamp fields:**

```json
{
  "created_at": "2024-01-15T10:30:00Z",
  "updated_at": "2024-01-16T14:22:00Z",
  "deleted_at": null
}
```

### Anti-Patterns

- **Inconsistent naming** — Mixing `created_at`, `createdAt`, and `CreateDate`
- **Verbs in URLs** — `/users/getById` instead of `/users/{id}`
- **Ignoring HTTP semantics** — Using POST for reads, GET for mutations
- **Leaky abstractions** — Exposing database schema in API structure
- **No versioning strategy** — Breaking changes without version control
- **Missing request IDs** — No way to trace requests across systems
- **Opaque errors** — Generic error messages without actionable details
- **Inconsistent null handling** — Sometimes omitting, sometimes `null`
