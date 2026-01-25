---
title: Cross-Functional Launch Coordination
impact: CRITICAL
tags: coordination, stakeholders, raci, alignment
---

## Cross-Functional Launch Coordination

**Impact: CRITICAL**

Launches fail at the seams between teams. Relentless coordination is the difference between success and chaos.

### The Launch Coordination Triad

```
              ┌─────────────┐
              │   PRODUCT   │
              │  (Captain)  │
              └──────┬──────┘
                     │
         ┌───────────┴───────────┐
         │                       │
    ┌────▼────┐             ┌────▼────┐
    │MARKETING│◄───────────►│ENGINEER │
    │         │             │  -ING   │
    └─────────┘             └─────────┘
```

Product is the captain, but Marketing and Engineering have veto power on their domains.

### RACI Matrix by Launch Phase

**Planning Phase (T-8 to T-4 weeks)**

| Activity | PM | PMM | Eng | Sales | Support | Exec |
|----------|----|----|-----|-------|---------|------|
| Launch brief creation | R | C | C | C | C | A |
| Tier decision | R | C | C | I | I | A |
| Timeline alignment | R | C | C | I | I | A |
| Success criteria | R | C | C | C | C | A |
| Resource allocation | R | C | C | I | I | A |

**Preparation Phase (T-4 to T-1 weeks)**

| Activity | PM | PMM | Eng | Sales | Support | Exec |
|----------|----|----|-----|-------|---------|------|
| Feature development | C | I | R | I | I | I |
| Content creation | C | R | I | C | I | I |
| Sales enablement | C | R | I | R | I | I |
| Support training | C | I | I | I | R | I |
| Beta management | R | C | C | I | C | I |

**Execution Phase (T-1 week to Launch)**

| Activity | PM | PMM | Eng | Sales | Support | Exec |
|----------|----|----|-----|-------|---------|------|
| Go/no-go decision | R | R | R | R | R | A |
| War room leadership | R | C | C | I | I | I |
| Launch deployment | C | I | R | I | I | I |
| External comms | C | R | I | I | I | A |
| Incident response | R | I | R | I | R | I |

*R = Responsible, A = Accountable, C = Consulted, I = Informed*

### Stakeholder Communication Cadence

| Tier | Daily Standup | Weekly Sync | Exec Update |
|------|---------------|-------------|-------------|
| **Tier 1** | Yes (all teams) | Yes | Weekly |
| **Tier 2** | Core team only | Yes | Bi-weekly |
| **Tier 3** | Async updates | As needed | At milestones |
| **Tier 4** | None | None | None |

### Good Example: Effective Coordination

```markdown
## Launch Coordination Plan: Enterprise SSO

### Core Team (Weekly Sync - Thursdays 2pm)
- PM: Sarah Chen (Captain)
- PMM: Mike Rodriguez
- Eng Lead: Priya Patel
- Sales Enablement: Tom Walsh
- Support Lead: Lisa Kim

### Extended Team (Informed via Slack #sso-launch)
- DevRel: James Wu
- Legal: Amanda Foster
- Security: David Park
- CS: Regional leads

### Communication Rhythm
| Cadence | Audience | Channel | Owner |
|---------|----------|---------|-------|
| Daily (T-2 weeks) | Core team | Standup | PM |
| Weekly | Extended team | Slack digest | PM |
| Bi-weekly | Exec sponsors | Email + 15min | PM |
| As needed | All-hands | Slack announcement | PM |

### Decision Rights
| Decision | Who Decides | Who Must Approve |
|----------|-------------|------------------|
| Launch date change | PM | Exec sponsor |
| Scope change | PM + Eng Lead | PM |
| Messaging change | PMM | PM |
| Go/no-go | Core team vote | Exec sponsor |

### Escalation Path
1. Core team member → PM (same day)
2. PM → Exec sponsor (within 24 hours)
3. Cross-functional conflict → Exec sponsor mediation
```

### Bad Example: Coordination Failure

```markdown
## What Went Wrong: Widget 2.0 Launch

### Red Flags Ignored:
- No single owner identified
- Marketing found out about features 1 week before launch
- Sales not trained until launch day
- Support documentation written by engineering
- No regular sync meetings scheduled
- Decisions made in hallway conversations

### Results:
- Support tickets 5x normal (untrained team)
- Sales couldn't answer customer questions
- Marketing blog post had wrong feature descriptions
- Launch delayed 2 weeks after "go" decision
- Exec blindsided by customer complaints

### Root Cause: No coordination framework
```

### Dependency Tracking

```
Launch Dependencies Map
═══════════════════════

Feature Complete (Eng)
        │
        ├──► Documentation Ready (Support)
        │           │
        │           └──► Support Training Complete
        │
        ├──► Demo Environment Ready (Eng)
        │           │
        │           └──► Sales Enablement Complete
        │
        └──► API Finalized (Eng)
                    │
                    └──► Integration Partner Ready

All paths must complete before Go/No-Go
```

### Handoff Protocols

| From | To | Handoff Artifact | Timing |
|------|----|--------------------|--------|
| Product | Marketing | Launch brief, feature specs | T-6 weeks |
| Product | Sales | Value prop, use cases, competitive | T-4 weeks |
| Product | Support | FAQ, troubleshooting guide | T-3 weeks |
| Engineering | Product | Technical constraints, risks | T-4 weeks |
| Marketing | Product | Content calendar, messaging | T-4 weeks |
| Marketing | Sales | Battlecards, one-pagers | T-2 weeks |

### Conflict Resolution Framework

```
Conflict Type           Resolution Path
─────────────           ───────────────
Timeline disagreement → PM arbitrates, exec approves
Scope disagreement    → PM decides with eng input
Messaging disagreement→ PMM decides with PM input
Resource conflict     → Exec sponsor decides
Quality vs. speed     → Eng lead has veto on quality
```

### Coordination Tooling

| Need | Tool | Owner |
|------|------|-------|
| Launch tracker | Notion/Asana/Linear | PM |
| Communication | Slack channel | PM |
| Documentation | Confluence/Notion | PM |
| Status updates | Weekly email | PM |
| Decision log | Shared doc | PM |

### Anti-Patterns

- **No single owner** — Shared ownership = no ownership
- **Siloed planning** — Teams discover conflicts at launch
- **Meeting overload** — 5 hours of syncs per day
- **Async only** — Some decisions need real-time discussion
- **No escalation path** — Conflicts fester
- **Late stakeholder inclusion** — "I didn't know about this launch"
- **Decision by committee** — Endless debate, no action
- **Verbal agreements** — Undocumented decisions create confusion
