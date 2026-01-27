---
title: API Specifications
impact: HIGH
tags: api, rest, openapi, documentation, contracts
---

## API Specifications

**Impact: HIGH**

API specs are contracts between services, teams, and external developers. Clear specs prevent integration bugs, reduce back-and-forth, and enable parallel development of frontend and backend.

### API Design Principles

1. **Consistency** — Same patterns across all endpoints
2. **Predictability** — Developers can guess behavior
3. **Discoverability** — Self-documenting responses
4. **Evolvability** — Can change without breaking clients
5. **Debuggability** — Errors help developers fix issues

### API Specification Components

| Component | Purpose | Required |
|-----------|---------|----------|
| **Endpoint** | URL path and HTTP method | Yes |
| **Description** | What this endpoint does | Yes |
| **Authentication** | Auth requirements | Yes |
| **Request** | Headers, params, body | Yes |
| **Response** | Success and error formats | Yes |
| **Examples** | Real request/response samples | Yes |
| **Rate Limits** | Throttling rules | If applicable |
| **Versioning** | API version info | Yes |

### Good API Spec Example (OpenAPI Style)

```yaml
# POST /workspaces/{workspace_id}/invitations
# Create a new workspace invitation

summary: Invite a user to a workspace
description: |
  Sends an invitation email to the specified address. The recipient
  can accept the invitation to join the workspace with the specified
  permission level. Invitations expire after 7 days.

  Requires Owner permission on the workspace.

tags:
  - Workspace Sharing

security:
  - BearerAuth: []

parameters:
  - name: workspace_id
    in: path
    required: true
    description: The unique identifier of the workspace
    schema:
      type: string
      format: uuid
    example: "550e8400-e29b-41d4-a716-446655440000"

requestBody:
  required: true
  content:
    application/json:
      schema:
        type: object
        required:
          - email
          - permission_level
        properties:
          email:
            type: string
            format: email
            description: Email address of the person to invite
            example: "newmember@company.com"
          permission_level:
            type: string
            enum: [viewer, editor, owner]
            description: Permission level to grant
            example: "editor"
          message:
            type: string
            maxLength: 500
            description: Optional personal message to include in email
            example: "Welcome to the team! Check out our Q4 planning workspace."

responses:
  201:
    description: Invitation created successfully
    content:
      application/json:
        schema:
          type: object
          properties:
            id:
              type: string
              format: uuid
            workspace_id:
              type: string
              format: uuid
            email:
              type: string
            permission_level:
              type: string
            invited_by:
              type: string
              format: uuid
            expires_at:
              type: string
              format: date-time
            created_at:
              type: string
              format: date-time
        example:
          id: "d290f1ee-6c54-4b01-90e6-d701748f0851"
          workspace_id: "550e8400-e29b-41d4-a716-446655440000"
          email: "newmember@company.com"
          permission_level: "editor"
          invited_by: "7c9e6679-7425-40de-944b-e07fc1f90ae7"
          expires_at: "2024-01-22T10:30:00Z"
          created_at: "2024-01-15T10:30:00Z"

  400:
    description: Invalid request
    content:
      application/json:
        schema:
          $ref: '#/components/schemas/Error'
        examples:
          invalid_email:
            summary: Invalid email format
            value:
              error:
                code: "INVALID_EMAIL"
                message: "The email address format is invalid"
                field: "email"
          workspace_full:
            summary: Workspace at member limit
            value:
              error:
                code: "WORKSPACE_FULL"
                message: "This workspace has reached its member limit (50)"
                limit: 50
                current: 50

  401:
    description: Authentication required
    content:
      application/json:
        schema:
          $ref: '#/components/schemas/Error'
        example:
          error:
            code: "UNAUTHORIZED"
            message: "Authentication token is missing or invalid"

  403:
    description: Permission denied
    content:
      application/json:
        schema:
          $ref: '#/components/schemas/Error'
        example:
          error:
            code: "FORBIDDEN"
            message: "Only workspace owners can send invitations"
            required_permission: "owner"
            your_permission: "editor"

  404:
    description: Workspace not found
    content:
      application/json:
        schema:
          $ref: '#/components/schemas/Error'
        example:
          error:
            code: "WORKSPACE_NOT_FOUND"
            message: "Workspace with ID '550e8400-...' does not exist"

  409:
    description: Conflict - user already invited or member
    content:
      application/json:
        schema:
          $ref: '#/components/schemas/Error'
        examples:
          already_member:
            summary: User is already a member
            value:
              error:
                code: "ALREADY_MEMBER"
                message: "This user is already a workspace member"
                existing_permission: "editor"
          pending_invitation:
            summary: Invitation already pending
            value:
              error:
                code: "INVITATION_PENDING"
                message: "An invitation is already pending for this email"
                invitation_id: "d290f1ee-6c54-4b01-90e6-d701748f0851"
                expires_at: "2024-01-22T10:30:00Z"

  429:
    description: Rate limit exceeded
    content:
      application/json:
        schema:
          $ref: '#/components/schemas/Error'
        example:
          error:
            code: "RATE_LIMITED"
            message: "Invitation limit exceeded. Try again later."
            retry_after: 3600
    headers:
      Retry-After:
        description: Seconds until rate limit resets
        schema:
          type: integer
        example: 3600

x-rate-limit:
  requests: 10
  window: 3600
  scope: workspace

x-changelog:
  - version: "2024-01-15"
    changes:
      - Added optional message field
  - version: "2023-11-01"
    changes:
      - Initial release
```

### Bad API Spec Example

```yaml
# POST /invite
# Invite user

request:
  email: string
  level: string

response:
  success: boolean
```

**Why it fails:**
- No endpoint description
- No authentication documented
- No parameter details or constraints
- Missing error responses
- No examples
- No versioning information
- Vague response schema

### Error Response Standards

**Consistent Error Schema:**

```json
{
  "error": {
    "code": "MACHINE_READABLE_CODE",
    "message": "Human readable explanation",
    "details": {
      "field": "problematic_field",
      "reason": "Specific validation failure"
    },
    "request_id": "req_abc123",
    "documentation_url": "https://docs.api.com/errors/CODE"
  }
}
```

**Standard Error Codes:**

| HTTP Status | Code | Use Case |
|-------------|------|----------|
| 400 | `VALIDATION_ERROR` | Invalid input |
| 400 | `INVALID_FORMAT` | Malformed JSON, wrong content type |
| 401 | `UNAUTHORIZED` | Missing or invalid auth |
| 401 | `TOKEN_EXPIRED` | Auth token expired |
| 403 | `FORBIDDEN` | Valid auth, insufficient permissions |
| 404 | `NOT_FOUND` | Resource doesn't exist |
| 409 | `CONFLICT` | Resource state conflict |
| 422 | `UNPROCESSABLE` | Valid format, invalid semantics |
| 429 | `RATE_LIMITED` | Too many requests |
| 500 | `INTERNAL_ERROR` | Server-side failure |
| 503 | `SERVICE_UNAVAILABLE` | Maintenance or overload |

### API Versioning Strategies

| Strategy | Example | Pros | Cons |
|----------|---------|------|------|
| **URL path** | `/v1/users` | Clear, cacheable | URL pollution |
| **Header** | `API-Version: 2024-01` | Clean URLs | Less visible |
| **Query param** | `/users?version=1` | Easy testing | Cache issues |
| **Content type** | `Accept: application/vnd.api.v1+json` | RESTful | Complex |

**Recommended:** URL path versioning for major versions, header-based for minor changes.

### Request/Response Examples

**List Endpoint Pattern:**

```json
// GET /workspaces/{id}/members?limit=20&cursor=abc123

// Response
{
  "data": [
    {
      "id": "user-1",
      "email": "user@example.com",
      "permission_level": "editor",
      "joined_at": "2024-01-10T10:00:00Z"
    },
    {
      "id": "user-2",
      "email": "admin@example.com",
      "permission_level": "owner",
      "joined_at": "2024-01-05T08:00:00Z"
    }
  ],
  "pagination": {
    "cursor": "def456",
    "has_more": true,
    "total_count": 47
  }
}
```

**Single Resource Pattern:**

```json
// GET /workspaces/{id}

// Response
{
  "data": {
    "id": "workspace-123",
    "name": "Q4 Planning",
    "created_at": "2024-01-01T00:00:00Z",
    "updated_at": "2024-01-15T10:30:00Z",
    "owner": {
      "id": "user-1",
      "email": "owner@example.com"
    },
    "member_count": 12,
    "settings": {
      "visibility": "private",
      "allow_guest_access": false
    }
  },
  "_links": {
    "self": "/workspaces/workspace-123",
    "members": "/workspaces/workspace-123/members",
    "invitations": "/workspaces/workspace-123/invitations"
  }
}
```

### Pagination Standards

| Style | Best For | Example |
|-------|----------|---------|
| **Cursor** | Large datasets, real-time data | `?cursor=eyJpZCI6MTIzfQ` |
| **Offset** | Stable datasets, jump-to-page | `?offset=40&limit=20` |
| **Keyset** | Ordered results, efficient DB | `?after_id=123&limit=20` |

**Always include:**
- Current page indicator
- Has more indicator
- Total count (if performant)

### API Documentation Checklist

```
Endpoint Documentation
├── □ HTTP method and path
├── □ Summary (one line)
├── □ Description (detailed)
├── □ Authentication requirements
├── □ Path parameters (with types, constraints)
├── □ Query parameters (with defaults)
├── □ Request body schema
├── □ Response schemas (all status codes)
├── □ Real examples (copy-pasteable)
└── □ Error codes and meanings

API-Wide Documentation
├── □ Authentication guide
├── □ Rate limiting policy
├── □ Versioning policy
├── □ Pagination guide
├── □ Error handling guide
├── □ Changelog
└── □ SDK/client library links
```

### Anti-Patterns

- **Undocumented endpoints** — "It's obvious from the code"
- **Example-free specs** — Schema without concrete examples
- **Error amnesia** — Only documenting 200 responses
- **Version neglect** — No versioning strategy until breaking change
- **Inconsistent naming** — `user_id` in one endpoint, `userId` in another
- **Kitchen sink responses** — Returning everything instead of what's needed
- **Chatty APIs** — Multiple calls needed for one logical operation
- **Undocumented limits** — Rate limits, pagination, max sizes not specified
- **Stale specs** — Documentation doesn't match implementation
- **Internal exposure** — Leaking implementation details in error messages
