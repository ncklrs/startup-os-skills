---
title: API Versioning and Deprecation
impact: HIGH
tags: versioning, deprecation, breaking-changes, migration
---

## API Versioning and Deprecation

**Impact: HIGH**

How you version and deprecate defines developer trust. Breaking changes without warning destroys relationships.

### Versioning Strategies Comparison

| Strategy | Example | Pros | Cons |
|----------|---------|------|------|
| **URL path** | `/v1/users` | Clear, cacheable | URL changes |
| **Header** | `API-Version: 2024-01` | Clean URLs | Hidden version |
| **Query param** | `/users?version=1` | Easy to test | Not RESTful |
| **Date-based** | `Stripe-Version: 2024-01-15` | Granular | Many versions |
| **No versioning** | Additive only | Simple | Limits evolution |

**Recommended: URL path versioning for major versions + date-based for minor**

### Version Lifecycle Stages

```
┌─────────┐    ┌──────────┐    ┌────────────┐    ┌───────────┐
│  ALPHA  │ →  │   BETA   │ →  │   STABLE   │ →  │DEPRECATED │ → SUNSET
│         │    │          │    │            │    │           │
│No SLA   │    │Limited   │    │Full SLA    │    │Migration  │
│May break│    │SLA       │    │Support     │    │period     │
└─────────┘    └──────────┘    └────────────┘    └───────────┘
```

### Breaking vs Non-Breaking Changes

**Non-breaking (safe to ship anytime):**

| Change Type | Example |
|-------------|---------|
| Add endpoint | New `POST /v1/refunds` |
| Add optional param | New `metadata` field |
| Add response field | New `updated_at` field |
| Expand enum values | New status `pending_review` |
| Increase limit | Rate limit 100→200/min |
| Add webhook event | New `invoice.finalized` |

**Breaking (requires new version):**

| Change Type | Example |
|-------------|---------|
| Remove endpoint | Delete `GET /v1/legacy` |
| Remove field | Remove `card_number` |
| Change field type | `amount`: string → integer |
| Add required param | New required `currency` |
| Remove enum value | Remove `cancelled` status |
| Change URL structure | `/users/{id}` → `/customers/{id}` |
| Change authentication | API key → OAuth only |

### Deprecation Timeline

**Recommended minimum timeline:**

| Stage | Duration | Actions |
|-------|----------|---------|
| **Announcement** | Day 0 | Blog post, changelog, email |
| **Soft deprecation** | 6 months | Warnings in responses |
| **Hard deprecation** | 12 months | Errors for new integrations |
| **Sunset** | 18-24 months | API removed |

**Communication cadence:**

```
Month 0:    Deprecation announced
Month 3:    Reminder email
Month 6:    Warning headers start
Month 9:    Final reminder
Month 12:   New integrations blocked
Month 18:   Final sunset warning
Month 24:   API sunset
```

### Deprecation Header Pattern

**Response headers for deprecated endpoints:**

```http
HTTP/1.1 200 OK
Deprecation: Sun, 01 Jan 2025 00:00:00 GMT
Sunset: Sun, 01 Jul 2025 00:00:00 GMT
Link: <https://docs.example.com/migration>; rel="deprecation"
```

**Warning in response body:**

```json
{
  "data": { ... },
  "warnings": [
    {
      "code": "deprecated_endpoint",
      "message": "This endpoint is deprecated and will be removed on 2025-07-01",
      "doc_url": "https://docs.example.com/v2-migration"
    }
  ]
}
```

### Migration Guide Structure

**Every breaking change needs a migration guide:**

```markdown
# Migrating from v1 to v2

## Overview
v2 introduces improved error handling and consistent naming.

## Timeline
- v2 released: January 1, 2024
- v1 deprecated: July 1, 2024
- v1 sunset: January 1, 2025

## Breaking Changes

### 1. Customer endpoint renamed

**Before (v1):**
```bash
GET /v1/users/{id}
```

**After (v2):**
```bash
GET /v2/customers/{id}
```

**Migration steps:**
1. Update endpoint URLs in your code
2. Update SDK to v2.0
3. Update field mappings (see below)

### 2. Response format changes

**Before (v1):**
```json
{"user_id": "123", "mail": "a@b.com"}
```

**After (v2):**
```json
{"id": "cus_123", "email": "a@b.com"}
```

## SDK Upgrade Guide
[Link to SDK migration docs]

## Need Help?
Contact support@example.com for migration assistance.
```

### Version Coexistence Strategy

**Running multiple versions:**

```
/v1/* → v1 handlers (maintenance mode)
/v2/* → v2 handlers (active development)

Shared: Auth, rate limiting, logging
Separate: Business logic, response formatting
```

**Feature flagging approach:**

```python
def get_user(user_id, version):
    user = db.get_user(user_id)

    if version == "v1":
        return format_v1_response(user)
    elif version == "v2":
        return format_v2_response(user)
```

### Changelog Best Practices

**Good changelog entry:**

```markdown
## 2024-01-15

### Added
- New `refunds` endpoint for processing refunds
- `metadata` field on all resources

### Changed
- Rate limits increased from 100 to 200 requests/minute
- `status` field now includes `pending_review` value

### Deprecated
- `GET /v1/users` - Use `GET /v2/customers` instead
  Sunset date: 2025-01-15
  [Migration guide →]

### Fixed
- Fixed pagination returning duplicate results
```

### Version Support Matrix

**Communicate clearly what's supported:**

| Version | Status | Support Level | End of Life |
|---------|--------|---------------|-------------|
| v3 | Current | Full support | TBD |
| v2 | Maintained | Security only | 2025-06-01 |
| v1 | Deprecated | None | 2024-12-31 |

### Handling Breaking Changes Gracefully

**Additive approach (preferred):**

```json
// Instead of changing existing fields...
{
  "status": "completed"  // Don't change this
}

// ...add new fields
{
  "status": "completed",
  "status_v2": {
    "code": "completed",
    "reason": "delivered"
  }
}
```

**Parallel endpoints during transition:**

```
GET /v1/users/{id}      # Old format, deprecated
GET /v2/customers/{id}  # New format, recommended
```

### Anti-Patterns

- **Silent breaking changes** — Changing behavior without versioning
- **Perpetual beta** — Using "beta" to avoid versioning commitment
- **Too many versions** — More than 2-3 active versions
- **No sunset dates** — Deprecated forever
- **Short deprecation cycles** — Less than 12 months
- **No migration path** — New version without upgrade guide
- **Breaking date-based versions** — Changing `2024-01-15` after release
- **Version in body** — Putting version in request body, not URL/header
- **Forced upgrades** — Sunsetting without adequate notice
