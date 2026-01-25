---
title: Technical Specifications
impact: HIGH
tags: technical-spec, architecture, system-design, engineering
---

## Technical Specifications

**Impact: HIGH**

Technical specs translate product requirements into engineering blueprints. They document architectural decisions, system interactions, and implementation approaches before code is written.

### When to Write Technical Specs

| Complexity | Spec Needed? | Approach |
|------------|--------------|----------|
| **Small** (<1 day) | No | Inline comments, PR description |
| **Medium** (1-5 days) | Lightweight | Brief design doc section |
| **Large** (1-2 weeks) | Yes | Full technical spec |
| **Critical** (any size) | Yes | Full spec + review |

**Always write a spec when:**
- Multiple teams/systems involved
- Breaking changes to existing APIs
- New infrastructure or services
- Security-sensitive features
- Performance-critical paths

### Technical Spec Structure

```markdown
# Technical Spec: [Feature Name]

## Overview
[2-3 sentence summary of what and why]

## Goals
[What this design achieves]

## Non-Goals
[What this design explicitly does NOT address]

## Background
[Context needed to understand the problem]

## Detailed Design
[The meat of the spec: architecture, components, flows]

## Data Model
[Schema changes, new models, relationships]

## API Design
[Endpoints, contracts, error handling]

## Security Considerations
[Auth, encryption, vulnerabilities, compliance]

## Observability
[Logging, metrics, alerting]

## Rollout Plan
[Deployment strategy, feature flags, migrations]

## Alternatives Considered
[Other approaches and why they were rejected]

## Open Questions
[Unresolved decisions]

## References
[Related docs, RFCs, PRDs]
```

### Good Technical Spec Example

```markdown
# Technical Spec: Workspace Sharing Service

## Overview
Build a sharing service that enables workspace owners to invite team members
with granular permissions. This supports the "Team Collaboration" initiative
targeting 25% increase in team plan conversions.

## Goals
- Enable workspace sharing with Owner/Editor/Viewer permissions
- Support up to 50 members per workspace
- Sub-second permission checks on workspace access
- Zero-downtime migration for existing workspaces

## Non-Goals
- Public link sharing (planned for v2)
- Cross-organization sharing
- Real-time collaboration features (separate initiative)

## Background
Currently, users share workspaces by sharing credentials (security risk) or
duplicating workspaces (data sync issues). Support tickets related to access
management are 40% of total volume.

See: [PRD: Team Workspace Sharing](link)

## Detailed Design

### Architecture Overview

┌─────────────────────────────────────────────────────────────┐
│                     API Gateway                             │
└────────────────────────┬────────────────────────────────────┘
                         │
         ┌───────────────┼───────────────┐
         │               │               │
         ▼               ▼               ▼
┌─────────────┐  ┌─────────────┐  ┌─────────────┐
│  Workspace  │  │   Sharing   │  │    Auth     │
│   Service   │  │   Service   │  │   Service   │
│  (existing) │  │    (new)    │  │  (existing) │
└──────┬──────┘  └──────┬──────┘  └─────────────┘
       │                │
       │         ┌──────┴──────┐
       │         │             │
       ▼         ▼             ▼
┌─────────────────────┐  ┌─────────────┐
│   PostgreSQL        │  │    Redis    │
│  (permissions)      │  │   (cache)   │
└─────────────────────┘  └─────────────┘

### Component Responsibilities

| Component | Responsibility |
|-----------|----------------|
| **Sharing Service** | Invitation CRUD, permission management |
| **Workspace Service** | Add permission checks to existing endpoints |
| **Auth Service** | Issue tokens with workspace claims |
| **Redis** | Cache permission lookups |

### Permission Model

Three permission levels (bitmask for efficient storage):

| Level | Value | Capabilities |
|-------|-------|--------------|
| Viewer | 1 | Read workspace, view history |
| Editor | 3 | Viewer + create/edit/delete content |
| Owner | 7 | Editor + manage members, settings, delete workspace |

Permission inheritance:
- Owner > Editor > Viewer
- Each level includes all lower permissions

### Invitation Flow

1. Owner submits invitation request (email, permission level)
2. Sharing Service validates:
   - Owner has permission
   - Email format valid
   - Workspace not at member limit
3. Generate invitation token (cryptographic random, 32 bytes)
4. Store invitation in pending_invitations table
5. Queue email via existing notification service
6. Invitee clicks link → validates token → creates membership
7. Token invalidated after use or expiration (7 days)

### Permission Check Flow

On every workspace request:

1. Extract workspace_id from request
2. Check Redis cache: `workspace:{id}:user:{user_id}`
3. If miss → query PostgreSQL → cache for 5 minutes
4. Deny if no permission record exists
5. Check operation against permission level
6. Log access attempt (success/failure)

Performance target: <10ms for cached, <50ms for uncached

## Data Model

### New Tables

-- Workspace memberships
CREATE TABLE workspace_memberships (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    workspace_id UUID NOT NULL REFERENCES workspaces(id) ON DELETE CASCADE,
    user_id UUID NOT NULL REFERENCES users(id) ON DELETE CASCADE,
    permission_level SMALLINT NOT NULL DEFAULT 1,
    invited_by UUID REFERENCES users(id),
    created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
    updated_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
    UNIQUE(workspace_id, user_id)
);

CREATE INDEX idx_memberships_workspace ON workspace_memberships(workspace_id);
CREATE INDEX idx_memberships_user ON workspace_memberships(user_id);

-- Pending invitations
CREATE TABLE workspace_invitations (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    workspace_id UUID NOT NULL REFERENCES workspaces(id) ON DELETE CASCADE,
    email VARCHAR(255) NOT NULL,
    permission_level SMALLINT NOT NULL DEFAULT 1,
    token VARCHAR(64) NOT NULL UNIQUE,
    invited_by UUID NOT NULL REFERENCES users(id),
    expires_at TIMESTAMP WITH TIME ZONE NOT NULL,
    created_at TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
    accepted_at TIMESTAMP WITH TIME ZONE
);

CREATE INDEX idx_invitations_token ON workspace_invitations(token);
CREATE INDEX idx_invitations_workspace ON workspace_invitations(workspace_id);

### Migration Strategy

1. Create new tables (non-blocking)
2. Backfill existing workspace owners into memberships table
3. Deploy permission checks in shadow mode (log but don't enforce)
4. Verify no legitimate access would be blocked
5. Enable enforcement with feature flag

## API Design

See [api-specs.md] for full OpenAPI specification.

Key endpoints:
- POST /workspaces/{id}/invitations - Create invitation
- GET /workspaces/{id}/members - List members
- PATCH /workspaces/{id}/members/{user_id} - Update permission
- DELETE /workspaces/{id}/members/{user_id} - Remove member

## Security Considerations

### Authentication
- All endpoints require valid JWT
- Invitation tokens are single-use, time-limited

### Authorization
- Permission checks on every workspace operation
- Owner-only operations: invite, remove, change permissions, delete workspace
- Audit log of all permission changes

### Data Protection
- Email addresses encrypted at rest
- Invitation tokens hashed in database
- Rate limiting: 10 invitations per hour per workspace

### Compliance
- GDPR: Include membership data in export/deletion
- SOC2: Audit trail requirements met

## Observability

### Metrics
- `sharing.invitations.sent` - Counter, by workspace
- `sharing.invitations.accepted` - Counter
- `sharing.permission_checks` - Histogram, by result (allowed/denied)
- `sharing.cache_hit_rate` - Gauge

### Logging
- All permission changes logged with actor, target, before/after
- Failed permission checks logged with request context

### Alerts
- Cache hit rate <80% for 5 minutes
- Permission check latency p99 >100ms
- Invitation accept rate <50% over 24 hours

## Rollout Plan

| Phase | Audience | Duration | Success Criteria |
|-------|----------|----------|------------------|
| Alpha | Internal team | 1 week | No blockers |
| Beta | 5% of Teams plan | 2 weeks | <0.1% error rate |
| GA | 100% | 1 week ramp | Metrics nominal |

Feature flag: `workspace_sharing_enabled`
Kill switch: Disable sharing service, fallback to owner-only access

## Alternatives Considered

### 1. Extend existing auth service
**Rejected:** Auth service is critical path, don't want to add complexity.
Separate service allows independent scaling and deployment.

### 2. Real-time permission sync (websockets)
**Rejected:** Adds complexity without clear user benefit.
5-minute cache TTL is acceptable for permission propagation.

### 3. Document-level permissions
**Rejected:** Out of scope for v1. Workspace-level granularity sufficient
based on user research.

## Open Questions

- [ ] Rate limit for invitations per workspace? (Proposed: 50/day)
- [ ] Allow users to leave workspaces? (Leaning yes)
- [ ] Notification when permissions changed? (Needs PM input)

## References

- [PRD: Team Workspace Sharing](link)
- [RFC: Permission System Evolution](link)
- [Auth Service Documentation](link)
```

### Bad Technical Spec Example

```markdown
# Tech Spec: Sharing

We need to add sharing to workspaces.

## Design
Add a new table for permissions. Add API endpoints for sharing.
Use Redis for caching.

## Security
Make it secure.

## Rollout
Deploy when ready.
```

**Why it fails:**
- No context or goals
- No architecture diagram
- Missing data model details
- No API contracts
- Vague security section
- No rollout strategy
- No alternatives considered

### Technical Spec Review Checklist

```
Architecture
├── □ Clear component diagram
├── □ Responsibilities well-defined
├── □ Integration points identified
├── □ Dependencies documented
└── □ Scalability considered

Data Model
├── □ Schema defined with types
├── □ Indexes specified
├── □ Migration strategy clear
└── □ Backwards compatibility addressed

API Design
├── □ Endpoints documented
├── □ Request/response formats
├── □ Error handling defined
└── □ Versioning strategy

Security
├── □ Auth/authz approach
├── □ Data protection
├── □ Threat model considered
└── □ Compliance requirements

Operational
├── □ Metrics defined
├── □ Logging strategy
├── □ Alerting thresholds
├── □ Runbook considerations
└── □ Rollback plan

Process
├── □ Reviewed by stakeholders
├── □ Open questions resolved
├── □ Alternatives documented
└── □ Timeline realistic
```

### Anti-Patterns

- **Design by committee** — Spec becomes vague to accommodate all opinions
- **Premature optimization** — Designing for scale you don't have yet
- **Missing context** — Spec without PRD link or business justification
- **Implementation masquerading** — Writing code in spec instead of design
- **Solo authorship** — No review from affected teams
- **Scope creep** — Spec expands to cover "nice to haves"
- **Analysis paralysis** — Perfect spec that never ships
- **Dead doc** — Spec not updated as implementation diverges
