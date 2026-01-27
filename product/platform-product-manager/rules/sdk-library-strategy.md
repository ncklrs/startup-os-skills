---
title: SDK and Library Strategy
impact: HIGH
tags: sdk, libraries, developer-tools, client-libraries
---

## SDK and Library Strategy

**Impact: HIGH**

SDKs are how most developers experience your API. They should feel native to each language ecosystem.

### SDK Value Proposition

**Why build SDKs:**

| Benefit | Without SDK | With SDK |
|---------|-------------|----------|
| **Time to integrate** | Hours | Minutes |
| **Error handling** | Manual parsing | Built-in |
| **Auth management** | DIY token refresh | Automatic |
| **Type safety** | None | Full types |
| **Updates** | Manual changes | Package update |
| **Best practices** | Hope they know | Enforced |

### Language Prioritization Framework

**Tier 1 - Essential (build first):**

| Language | Why | Ecosystem |
|----------|-----|-----------|
| **Python** | Data, ML, scripting | pip |
| **JavaScript/Node** | Web, serverless | npm |
| **curl/HTTP** | Universal testing | N/A |

**Tier 2 - Growth (build second):**

| Language | Why | Ecosystem |
|----------|-----|-----------|
| **Go** | Cloud-native, infra | go modules |
| **Ruby** | Web apps, Rails | gem |
| **Java** | Enterprise | Maven/Gradle |

**Tier 3 - Expand (based on demand):**

| Language | Why | Ecosystem |
|----------|-----|-----------|
| **PHP** | WordPress, legacy web | Composer |
| **C#/.NET** | Enterprise, Microsoft | NuGet |
| **Swift** | iOS native | Swift Package Manager |
| **Kotlin** | Android native | Maven/Gradle |
| **Rust** | Systems, performance | Cargo |

### SDK Generation Strategies

| Strategy | Pros | Cons | Best For |
|----------|------|------|----------|
| **Hand-written** | Native feel, optimized DX | Expensive to maintain | Core SDKs, Tier 1 languages |
| **Code generation** | Consistent, easy to update | Can feel generic | Many languages, rapid iteration |
| **OpenAPI generators** | Industry standard | Limited customization | Getting started |
| **Hybrid** | Best of both | Complexity | Scale with quality |

**Recommended approach:**
- Tier 1: Hand-written for best DX
- Tier 2: Generated with hand-written improvements
- Tier 3: Generated from OpenAPI spec

### SDK Design Principles

**1. Follow language conventions:**

```python
# Python: snake_case, context managers
with client.batch() as batch:
    batch.create_user(email="user@example.com")
    batch.create_order(user_id="usr_123")
```

```javascript
// JavaScript: camelCase, promises/async
const user = await client.users.create({
  email: 'user@example.com'
});
```

```go
// Go: exported types, explicit errors
user, err := client.Users.Create(ctx, &CreateUserParams{
    Email: "user@example.com",
})
```

**2. Consistent resource access pattern:**

```python
# Resource-based access
client.users.create(...)
client.users.retrieve("usr_123")
client.users.update("usr_123", ...)
client.users.delete("usr_123")
client.users.list(limit=10)

# Nested resources
client.users.orders.list("usr_123")
```

**3. Type safety where available:**

```typescript
// TypeScript: Full type definitions
interface CreateUserParams {
  email: string;
  name?: string;
  metadata?: Record<string, string>;
}

interface User {
  id: string;
  email: string;
  name: string | null;
  created_at: string;
}

const user: User = await client.users.create({
  email: 'user@example.com'
});
```

### SDK Feature Checklist

| Feature | Priority | Notes |
|---------|----------|-------|
| **Authentication** | Critical | API key, OAuth support |
| **Automatic retries** | Critical | Exponential backoff |
| **Error handling** | Critical | Typed exceptions |
| **Request/response logging** | High | Debug mode |
| **Pagination helpers** | High | Iterate without manual paging |
| **Idempotency support** | High | Built-in key generation |
| **Webhook verification** | High | Signature validation |
| **Type definitions** | High | TypeScript, Python types |
| **Timeout configuration** | Medium | Request-level timeouts |
| **Proxy support** | Medium | Enterprise requirements |
| **Custom HTTP client** | Medium | Testing, customization |

### Error Handling Pattern

**Good SDK error design:**

```python
from example import Client, APIError, AuthenticationError, RateLimitError

client = Client("sk_test_...")

try:
    user = client.users.create(email="invalid")
except AuthenticationError as e:
    # Invalid API key
    print(f"Auth failed: {e.message}")
except RateLimitError as e:
    # Rate limited - retry after delay
    print(f"Rate limited. Retry after {e.retry_after}s")
except APIError as e:
    # General API error
    print(f"API error: {e.code} - {e.message}")
    print(f"Request ID: {e.request_id}")
```

**Error class hierarchy:**

```
ExampleError (base)
├── APIError
│   ├── AuthenticationError
│   ├── AuthorizationError
│   ├── NotFoundError
│   ├── ValidationError
│   └── RateLimitError
├── NetworkError
│   ├── TimeoutError
│   └── ConnectionError
└── SDKError
    └── ConfigurationError
```

### Pagination Patterns

**Good pagination (auto-pagination):**

```python
# Iterate all users without manual paging
for user in client.users.list(limit=100):
    process(user)

# Or with async
async for user in client.users.list():
    await process(user)
```

**Manual pagination access:**

```python
page = client.users.list(limit=10)
print(page.data)           # List of users
print(page.has_more)       # Boolean
print(page.next_page())    # Get next page
```

### SDK Documentation Requirements

**Per-language docs should include:**

1. Installation instructions
2. Authentication setup
3. Basic usage example
4. Error handling
5. Advanced configuration
6. Migration guides (version upgrades)

**Example structure:**

```markdown
# Python SDK

## Installation
pip install example-sdk

## Quick Start
```python
from example import Client
client = Client("sk_test_...")
```

## Authentication
[Details on API keys, OAuth, etc.]

## Resources
- [Users](/sdk/python/users)
- [Orders](/sdk/python/orders)

## Error Handling
[Exception types and handling]

## Configuration
[Timeouts, retries, logging]
```

### SDK Versioning Strategy

| API Change | SDK Change | Semver |
|------------|------------|--------|
| New endpoint | New method | Minor (1.x.0) |
| New optional param | New optional param | Minor (1.x.0) |
| New required param | Breaking change | Major (x.0.0) |
| Endpoint removed | Method removed | Major (x.0.0) |
| Bug fix | Bug fix | Patch (1.0.x) |

**Version support policy:**

```
Current major version:    Full support
Previous major version:   Security fixes only (12 months)
Older versions:           Unsupported
```

### Testing Strategy for SDKs

| Test Type | Purpose | Coverage |
|-----------|---------|----------|
| **Unit tests** | SDK logic | 90%+ |
| **Integration tests** | Real API calls | Key flows |
| **Generated tests** | OpenAPI compliance | All endpoints |
| **Example tests** | Docs accuracy | All examples |

### Anti-Patterns

- **Thin wrappers** — SDK that just wraps HTTP with no added value
- **Non-idiomatic code** — Ruby SDK that feels like Java
- **Missing types** — No TypeScript definitions for JS
- **Inconsistent naming** — Different patterns across languages
- **No error context** — Generic errors without details
- **Version lock** — SDK pinned to specific API version
- **Giant SDK** — Including everything vs. modular packages
- **No changelog** — Updates without migration guidance
