---
title: Feature Flags and Rollout Plans
impact: MEDIUM-HIGH
tags: feature-flags, rollout, deployment, experiments, releases
---

## Feature Flags and Rollout Plans

**Impact: MEDIUM-HIGH**

Feature flags and rollout plans turn risky big-bang releases into controlled, reversible deployments. They enable experimentation, gradual rollouts, and instant rollbacks.

### Why Feature Flags

1. **Risk reduction** — Limit blast radius of bugs
2. **Faster iteration** — Ship code without exposing features
3. **Experimentation** — A/B test with real users
4. **Operational control** — Disable features without deploys
5. **Customer control** — Enable for specific accounts

### Feature Flag Types

| Type | Purpose | Lifespan | Example |
|------|---------|----------|---------|
| **Release** | Gate unreleased features | Short (weeks) | `sharing_v2_enabled` |
| **Experiment** | A/B testing | Short (days-weeks) | `checkout_flow_experiment` |
| **Ops** | Circuit breakers, load shedding | Permanent | `heavy_report_enabled` |
| **Permission** | Plan/role-based access | Permanent | `enterprise_analytics` |
| **Kill Switch** | Emergency disable | Permanent | `third_party_integration` |

### Feature Flag Naming Convention

```
{scope}_{feature}_{purpose}

Examples:
- release_workspace_sharing_enabled
- experiment_pricing_page_variant
- ops_batch_processing_enabled
- permission_custom_domains_access
- kill_switch_stripe_integration
```

### Feature Flag Specification Template

```markdown
## Feature Flag: [Name]

### Overview
| Property | Value |
|----------|-------|
| Flag Name | `release_workspace_sharing_enabled` |
| Type | Release |
| Owner | Product Team |
| Created | 2024-01-15 |
| Expected Removal | 2024-03-01 |

### Description
Gates access to the new workspace sharing feature, including:
- Invite modal in workspace header
- Members tab in workspace settings
- Sharing-related API endpoints

### Targeting Rules

| Stage | Audience | Percentage | Start Date |
|-------|----------|------------|------------|
| Internal | @company.com emails | 100% | Jan 15 |
| Alpha | Specific accounts (list below) | 100% | Jan 22 |
| Beta | Teams plan users | 10% → 50% | Feb 1 |
| GA | All users | 100% | Feb 15 |

**Alpha Account List:**
- Acme Corp (acct_123)
- Beta Inc (acct_456)
- Gamma LLC (acct_789)

### Fallback Behavior
When flag is OFF:
- "Invite" button hidden in workspace header
- Sharing API endpoints return 404
- Direct links to sharing pages redirect to workspace

### Dependencies
| Dependency | Status |
|------------|--------|
| Sharing Service deployed | Required |
| Email templates ready | Required |
| Analytics events tracked | Required |

### Rollback Criteria
Immediately disable if:
- Error rate >1% on sharing endpoints
- >50 support tickets related to sharing
- Data integrity issues detected

### Metrics to Monitor
- `sharing.invitations.sent` — Expected increase
- `sharing.invitations.errors` — Should stay <0.1%
- `workspace.load_time` — Should not increase >100ms
- Support ticket volume — Monitor for sharing issues

### Cleanup Plan
After 100% rollout for 2 weeks:
1. Remove flag checks from code
2. Remove flag from configuration
3. Update documentation
4. Archive this spec
```

### Rollout Plan Template

```markdown
# Rollout Plan: [Feature Name]

## Overview
| Property | Value |
|----------|-------|
| Feature | Workspace Sharing |
| PRD Link | [Link] |
| Tech Spec Link | [Link] |
| Feature Flag | `release_workspace_sharing_enabled` |
| Target GA Date | February 15, 2024 |

## Pre-Launch Checklist

### Engineering Readiness
- [ ] Code merged to main
- [ ] Feature flag created and tested
- [ ] Database migrations complete
- [ ] Performance testing passed
- [ ] Security review approved
- [ ] Monitoring/alerting configured

### Product Readiness
- [ ] User documentation published
- [ ] Help center articles updated
- [ ] In-app tooltips configured
- [ ] Email templates approved

### Support Readiness
- [ ] Support team briefed
- [ ] FAQ document created
- [ ] Escalation path defined
- [ ] Known issues documented

### Marketing Readiness
- [ ] Announcement blog post drafted
- [ ] Social media posts scheduled
- [ ] Email campaign prepared (if applicable)

## Rollout Stages

### Stage 1: Internal Testing (Jan 15-21)

**Audience:** Internal employees only
**Goal:** Validate core functionality, find obvious bugs

| Task | Owner | Status |
|------|-------|--------|
| Enable for @company.com | Eng | |
| Conduct internal testing | QA | |
| Fix critical bugs | Eng | |
| Document known issues | PM | |

**Go/No-Go Criteria:**
- [ ] No critical bugs
- [ ] Core flows work end-to-end
- [ ] Internal team sign-off

### Stage 2: Alpha (Jan 22-31)

**Audience:** 10 design partner accounts
**Goal:** Validate with real users, gather feedback

| Task | Owner | Status |
|------|-------|--------|
| Enable for alpha accounts | Eng | |
| Schedule feedback calls | PM | |
| Monitor error rates | Eng | |
| Iterate on feedback | Team | |

**Alpha Accounts:**
1. Acme Corp — Sarah (PM), sarah@acme.com
2. Beta Inc — John (CTO), john@beta.com
3. [...]

**Go/No-Go Criteria:**
- [ ] NPS >30 from alpha users
- [ ] Error rate <0.5%
- [ ] No data integrity issues
- [ ] Alpha user sign-off

### Stage 3: Beta (Feb 1-14)

**Audience:** Teams plan users, gradual percentage rollout
**Goal:** Validate at scale, stress test

| Day | Percentage | Users | Notes |
|-----|------------|-------|-------|
| Feb 1 | 5% | ~500 | Initial beta |
| Feb 5 | 10% | ~1,000 | If no issues |
| Feb 8 | 25% | ~2,500 | Expand |
| Feb 12 | 50% | ~5,000 | Final beta |

**Monitoring:**
- Hourly check: Error rates, latency
- Daily check: Support tickets, user feedback
- Weekly: Analytics review

**Pause/Rollback Triggers:**
- Error rate >1% for 30 minutes
- Latency p99 >500ms for 30 minutes
- >10 support tickets/hour related to feature
- Any data corruption detected

### Stage 4: General Availability (Feb 15)

**Audience:** All users
**Goal:** Feature fully launched

| Task | Owner | Status |
|------|-------|--------|
| Ramp to 100% | Eng | |
| Publish announcement | Marketing | |
| Monitor closely (48 hours) | Eng | |
| Begin flag cleanup | Eng | |

## Rollback Plan

### Rollback Procedure

1. **Decision Maker:** On-call eng or PM
2. **Action:** Disable flag in LaunchDarkly
3. **Impact:** Feature immediately hidden for all users
4. **Data:** No data loss; existing memberships preserved
5. **Communication:** Status page update within 15 minutes

### Rollback Communication Templates

**Status Page (Incident):**
```
We are temporarily disabling workspace sharing while we investigate
an issue. Existing workspace configurations are preserved. We
expect to re-enable the feature within [timeframe].
```

**Customer Email (if needed):**
```
Subject: Temporary pause on Workspace Sharing

We've temporarily paused the new workspace sharing feature while
we address an issue we discovered. Your existing workspace setup
is safe and will work normally when we re-enable the feature.

We expect to have this resolved within [timeframe].
```

## Post-Launch

### Success Criteria (2 weeks post-GA)
- [ ] 20% of Teams accounts have used sharing
- [ ] Workspace duplication down 30%
- [ ] Access-related tickets down 25%
- [ ] No P0/P1 bugs outstanding

### Cleanup Tasks
- [ ] Remove feature flag from code (by Mar 1)
- [ ] Archive rollout documentation
- [ ] Retrospective meeting scheduled
- [ ] Share learnings with team
```

### Rollout Strategies

| Strategy | Use Case | Risk Level |
|----------|----------|------------|
| **Big Bang** | Simple changes, low risk | High |
| **Percentage** | Gradual exposure | Medium |
| **Ring** | Employee → Beta → GA | Low |
| **Geography** | Test in single region first | Low |
| **Account** | Specific customers | Very Low |
| **Time-based** | Enable during low traffic | Low |

### Good Rollout Example

```markdown
## Rollout: New Checkout Flow

### Strategy: Ring-based with percentage

Ring 1 (Week 1): Internal employees
├── 100% of @company.com
├── Validate all payment paths
└── Success: No checkout failures

Ring 2 (Week 2): Friendly customers
├── 50 accounts who opted in
├── Collect qualitative feedback
└── Success: NPS >40, no critical bugs

Ring 3 (Week 3): Canary
├── 1% of production traffic
├── Compare conversion rate to control
├── Success: Conversion within 5% of baseline

Ring 4 (Week 4): Gradual rollout
├── 1% → 5% → 10% → 25% → 50% → 100%
├── 24 hours between each stage
└── Success: Conversion improved or neutral

Rollback: Instant flag disable, fallback to old checkout
```

### Bad Rollout Example

```markdown
## Rollout: New Checkout Flow

Ship it on Monday. If there are problems, we'll fix them.
```

**Why it fails:**
- No staged rollout
- No success criteria
- No monitoring plan
- No rollback plan
- No communication plan

### Feature Flag Hygiene

| Lifecycle Stage | Action |
|-----------------|--------|
| **Creation** | Document purpose, owner, expected removal date |
| **Active** | Review monthly, update targeting rules |
| **Stale** | After 90 days at 100%, schedule cleanup |
| **Removal** | Delete flag, remove code checks, archive docs |

**Technical Debt Warning Signs:**
- Flags older than 6 months
- Flags with no recent evaluations
- Flags with no documented owner
- Code checking multiple flags for same feature

### Anti-Patterns

- **Flag forever** — Never removing flags, code becomes unmaintainable
- **Flag explosion** — Too many flags, impossible to understand state
- **No rollback testing** — Rollback plan not actually tested
- **Big bang despite flags** — Having flags but going 0→100%
- **Flag as security** — Using flags instead of proper auth
- **Coupling flags** — Flag A requires Flag B, creating dependencies
- **Silent rollout** — No monitoring during gradual rollout
- **Premature celebration** — Declaring success before cleanup
- **No owner** — Flags without clear ownership decay
- **Flag naming chaos** — Inconsistent names impossible to search
