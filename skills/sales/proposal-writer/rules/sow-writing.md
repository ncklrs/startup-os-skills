---
title: Statement of Work (SOW) Writing
impact: HIGH
tags: sow, scope, deliverables, contract, implementation
---

## Statement of Work (SOW) Writing

**Impact: HIGH**

The SOW is the contract that defines success. It protects both parties and sets expectations for delivery.

### SOW vs. Proposal

| Element | Proposal | SOW |
|---------|----------|-----|
| **Purpose** | Persuade | Define |
| **Tone** | Inspiring | Precise |
| **Language** | Marketing | Legal/operational |
| **Flexibility** | High | Low |
| **When** | Pre-decision | Post-verbal/signature |

### Essential SOW Components

```
┌─────────────────────────────────────────────────────────────┐
│                 STATEMENT OF WORK                           │
├─────────────────────────────────────────────────────────────┤
│  1. Parties & Effective Date                                │
│  2. Background & Objectives                                 │
│  3. Scope of Work (detailed)                                │
│  4. Deliverables (specific, measurable)                     │
│  5. Timeline & Milestones                                   │
│  6. Responsibilities (both parties)                         │
│  7. Assumptions & Dependencies                              │
│  8. Out of Scope (explicit exclusions)                      │
│  9. Acceptance Criteria                                     │
│ 10. Change Management Process                               │
│ 11. Fees & Payment Terms                                    │
│ 12. Term & Termination                                      │
└─────────────────────────────────────────────────────────────┘
```

### Good Example: Clear SOW Sections

```markdown
# Statement of Work
## SecretStash Enterprise Implementation

**Client:** TechCorp, Inc.
**Vendor:** SecretStash, Inc.
**Effective Date:** April 1, 2025
**SOW Number:** SOW-2025-0142

---

## 1. Background & Objectives

TechCorp ("Client") requires implementation of SecretStash Enterprise
to centralize secrets management across its engineering organization.

**Primary Objectives:**
1. Centralize 100% of production secrets within SecretStash by May 31
2. Achieve SOC 2 compliance readiness for secrets management by June 15
3. Reduce developer onboarding time from 15 days to 4 days by June 30

---

## 2. Scope of Work

### 2.1 Phase 1: Foundation (Weeks 1-2)

| Task | Description | Owner |
|------|-------------|-------|
| 2.1.1 | Provision SecretStash tenant and configure SSO | SecretStash |
| 2.1.2 | Install CLI tools on CI/CD runners | Client |
| 2.1.3 | Configure RBAC policies per provided org chart | SecretStash |
| 2.1.4 | Migrate Vault 1 (staging) secrets | Joint |

**Phase 1 Exit Criteria:**
- [ ] SSO authentication functional for all users
- [ ] CI/CD integration tested in staging environment
- [ ] 100% of staging secrets migrated

### 2.2 Phase 2: Production Migration (Weeks 3-4)

| Task | Description | Owner |
|------|-------------|-------|
| 2.2.1 | Migrate production secrets (Vault 2-5) | Joint |
| 2.2.2 | Configure automated rotation policies | SecretStash |
| 2.2.3 | Implement audit logging and alerts | SecretStash |
| 2.2.4 | Execute production validation testing | Joint |

**Phase 2 Exit Criteria:**
- [ ] 100% of production secrets migrated
- [ ] Rotation policies active for database credentials
- [ ] Audit logs flowing to Client's SIEM

### 2.3 Phase 3: Enablement (Weeks 5-6)

| Task | Description | Owner |
|------|-------------|-------|
| 2.3.1 | Deliver admin training (4 hours) | SecretStash |
| 2.3.2 | Deliver developer training (2 hours) | SecretStash |
| 2.3.3 | Create internal documentation | Client |
| 2.3.4 | Conduct go-live readiness review | Joint |

---

## 3. Deliverables

| # | Deliverable | Format | Due Date |
|---|-------------|--------|----------|
| D1 | Project kickoff deck | PDF | Week 1, Day 1 |
| D2 | Migration runbook | Confluence doc | Week 2, Day 5 |
| D3 | RBAC policy documentation | SecretStash export | Week 2, Day 5 |
| D4 | Training materials (admin) | PDF + video | Week 5, Day 1 |
| D5 | Training materials (developer) | PDF + video | Week 5, Day 1 |
| D6 | Implementation summary report | PDF | Week 6, Day 5 |

---

## 4. Client Responsibilities

Client agrees to provide:

| Responsibility | Required By |
|----------------|-------------|
| Designated project manager with authority | Week 1, Day 1 |
| Access to staging and production environments | Week 1, Day 3 |
| Org chart for RBAC configuration | Week 1, Day 3 |
| Inventory of all secrets to migrate | Week 1, Day 5 |
| Availability for 2x weekly sync calls | Throughout |
| Testing resources for UAT | Week 4-5 |

**Note:** Delays in Client responsibilities may impact timeline
and trigger the Change Management process (Section 8).

---

## 5. Assumptions

This SOW is based on the following assumptions:

1. Total secrets to migrate: ≤ 500
2. Number of environments: ≤ 5
3. CI/CD platform: GitHub Actions (as discussed)
4. SSO provider: Okta (active directory sync enabled)
5. Client team availability: minimum 10 hours/week
6. No custom integration development required

If any assumption proves incorrect, scope and timeline may be
adjusted via Change Order.

---

## 6. Out of Scope

The following are explicitly excluded from this engagement:

- Migration of secrets from systems not identified in discovery
- Custom SDK development
- Integration with systems other than GitHub Actions and Okta
- Ongoing managed services post-implementation
- Security audits or penetration testing
- Legacy system decommissioning

---

## 7. Acceptance Criteria

Each phase is considered accepted when:

1. Exit criteria checklist is complete
2. Client project manager provides written sign-off
3. No Severity 1 issues remain open

If Client does not provide acceptance or rejection within
5 business days of phase completion, phase is deemed accepted.

---

## 8. Change Management

Changes to scope, timeline, or deliverables require:

1. Written Change Request submitted by either party
2. Impact assessment (scope, timeline, cost) within 3 business days
3. Written approval from both project managers
4. Amendment to this SOW

**Change Request rates:**
- Additional configuration: $200/hour
- Custom development: $250/hour
- Extended timeline: As quoted per Change Request
```

### Bad Example: Vague SOW

```markdown
# Statement of Work

## Project Overview

SecretStash will implement our platform for TechCorp.

## Scope

- Install and configure SecretStash
- Migrate customer secrets
- Provide training
- Support go-live

## Timeline

Project will be completed in approximately 6 weeks.

## Deliverables

- Working SecretStash implementation
- Training for the team
- Documentation

## Pricing

$12,000 for implementation services.
```

**Why it fails:**
- No specific tasks or owners
- No measurable deliverables
- Vague timeline with no milestones
- Missing assumptions and out-of-scope
- No client responsibilities
- No acceptance criteria
- No change management process
- Sets up scope disagreements

### Scope Protection Strategies

**Be specific about quantities:**
```
VAGUE:  "Migrate all secrets"
BETTER: "Migrate up to 500 secrets across 5 environments"
```

**Define effort limits:**
```
VAGUE:  "Provide training"
BETTER: "Deliver 2 training sessions, 2 hours each, for up to
        25 participants per session"
```

**Call out exclusions explicitly:**
```
"This engagement specifically excludes:
 - Custom integration development
 - Secrets stored in systems not identified in Appendix A
 - Ongoing support beyond 30 days post go-live"
```

### Timeline & Milestone Best Practices

| Element | Guidance |
|---------|----------|
| **Phase duration** | 2-4 weeks per phase is manageable |
| **Buffer** | Build 10-20% buffer for dependencies |
| **Dependencies** | Show what must happen before next phase |
| **Critical path** | Identify items that can't slip |
| **Milestones** | Tied to deliverables, not dates alone |

### RACI for SOW Tasks

Define ownership clearly:

| Task | SecretStash | Client |
|------|-------------|--------|
| Platform configuration | R, A | C, I |
| Secret inventory | C, I | R, A |
| Migration execution | R, A | C |
| UAT testing | I | R, A |
| Go-live decision | C | R, A |

**R** = Responsible, **A** = Accountable, **C** = Consulted, **I** = Informed

### Payment Milestone Options

| Structure | Best For | Example |
|-----------|----------|---------|
| **Fixed price** | Well-defined scope | $12,000 total |
| **Time & materials** | Uncertain scope | $200/hr, capped at $15,000 |
| **Milestone-based** | Phased delivery | 40% kickoff, 40% go-live, 20% acceptance |
| **Hybrid** | Complex projects | Fixed base + T&M for changes |

### Anti-Patterns

- **Scope creep language** — "And other duties as required"
- **Undefined deliverables** — "Documentation" with no spec
- **One-sided responsibilities** — All obligations on vendor
- **Missing change process** — No way to handle inevitable changes
- **Vague acceptance** — "When customer is satisfied"
- **Forgetting dependencies** — Your timeline depends on their action
