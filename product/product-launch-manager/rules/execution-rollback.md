---
title: Rollback and Contingency Planning
impact: CRITICAL
tags: execution, rollback, contingency, risk
---

## Rollback and Contingency Planning

**Impact: CRITICAL**

Hope is not a strategy. Every launch needs a clear rollback plan and contingencies for when things go wrong.

### Rollback Decision Matrix

| Scenario | Severity | Rollback? | Decision Maker |
|----------|----------|-----------|----------------|
| Error rate > 5% | Critical | Yes - Immediate | Eng Lead |
| Security vulnerability | Critical | Yes - Immediate | Security Lead |
| Data corruption | Critical | Yes - Immediate | Eng Lead |
| P0 incident unresolved > 30 min | High | Yes | PM + Eng Lead |
| Error rate 1-5%, stable | Medium | Assess | PM |
| Support volume > 10x | Medium | Assess | PM + Support Lead |
| Negative press, feature works | Low | No | Continue monitoring |
| Single customer complaint | Low | No | Continue monitoring |

### Rollback Types

| Type | Speed | Scope | When to Use |
|------|-------|-------|-------------|
| **Feature flag** | Seconds | Single feature | Preferred method |
| **Gradual rollback** | Minutes | Percentage of users | Minimize disruption |
| **Full rollback** | Minutes-Hours | Entire deployment | Severe issues |
| **Database rollback** | Hours | Data + code | Data corruption |

### Rollback Readiness Checklist

```markdown
## Pre-Launch Rollback Verification

□ Feature flag configured and tested
□ Rollback command documented
□ Rollback tested in staging
□ Database rollback tested (if applicable)
□ Rollback runbook reviewed by on-call
□ Monitoring alerts set for rollback triggers
□ Communication templates ready
□ Decision authority clear

## Rollback Command
Feature flag: `./scripts/toggle-feature.sh sso-launch off`
Verify: Check [dashboard link] for flag status

## Estimated Rollback Time
- Feature flag: < 1 minute
- Full effect: < 5 minutes
- Verification: 10 minutes
```

### Good Example: Clean Rollback

```markdown
## Rollback Incident Report: Workflow Automation

**Timeline:**
- 09:15 - Feature launched, all green
- 09:45 - Error rate climbing (0.2% → 0.8%)
- 10:00 - Identified: Edge case in EU data center
- 10:05 - Decision: Attempt hotfix, 15 min timeout
- 10:20 - Hotfix not ready, error rate at 1.5%
- 10:22 - PM: "Initiating rollback"
- 10:23 - Eng Lead: "ROLLBACK CONFIRMED"
- 10:24 - Feature flag disabled
- 10:25 - Marketing campaigns paused
- 10:27 - Support team notified, canned response activated
- 10:30 - Error rate returning to baseline
- 10:35 - Rollback verified complete
- 10:40 - Customer communication sent

**What Went Well:**
- Clear decision criteria (1.5% > 1% threshold)
- Fast rollback execution (< 5 minutes)
- Good communication throughout
- No customer-facing outage

**Root Cause:**
- EU data center timezone handling edge case
- Not covered in beta (no EU beta users)

**Relaunch Plan:**
- Fix deployed to staging: 10/15
- EU-specific beta: 10/16-10/18
- Relaunch: 10/19
```

### Bad Example: Rollback Chaos

```markdown
## Rollback Disaster: Report Builder

**What Happened:**
- 09:00 - Launch
- 10:00 - Error rate at 3%, rising
- 10:15 - Support: "Should we rollback?"
- 10:20 - PM in meeting, no response
- 10:30 - Eng: "I could rollback but need approval"
- 10:45 - Error rate at 7%
- 11:00 - Exec: "Why is Twitter angry?"
- 11:10 - PM: "Who can make the rollback decision?"
- 11:20 - Rollback attempted, failed (untested)
- 11:45 - Rollback finally successful
- 12:00 - No customer communication prepared

**Impact:**
- 2.5 hours of degraded experience
- 47 angry support tickets
- 3 enterprise customers escalated to exec
- 2 tweets from tech press

**Root Causes:**
- No clear rollback authority
- Rollback never tested
- No pre-written communication
- PM not available during launch
```

### Contingency Planning Matrix

| Risk | Likelihood | Impact | Mitigation | Contingency |
|------|------------|--------|------------|-------------|
| High error rate | Medium | High | Thorough testing | Feature flag rollback |
| Support overwhelm | Medium | Medium | Pre-launch enablement | Temporary staff, queue priority |
| Negative press | Low | High | Embargo, press prep | Crisis comms plan |
| Competitor response | Medium | Low | Battlecards ready | Sales alert, response talking points |
| Infrastructure failure | Low | Critical | Load testing | Rollback + status page |
| Security vulnerability | Low | Critical | Security review | Immediate rollback, incident response |

### Contingency Communication Templates

**Internal Rollback Announcement:**
```
🔴 ROLLBACK COMPLETE

The [Feature] launch has been rolled back due to [brief reason].

What happened:
- [1-2 sentence description]

What we're doing:
- Engineering investigating root cause
- ETA for fix assessment: [time]
- Relaunch target: TBD pending fix

What you should do:
- Sales: Pause outreach about [Feature]
- Support: Use canned response #rollback-[feature]
- Marketing: Campaigns paused automatically

Next update: [time]
```

**Customer Communication (Major Issue):**
```
Subject: Update on [Feature] - Temporary Availability

Hi [Name],

Earlier today we launched [Feature]. Some users experienced
[brief issue description], so we've temporarily rolled back
the feature while we make it right.

What this means for you:
- [Feature] is temporarily unavailable
- Your existing data/settings are unaffected
- We expect to relaunch within [timeframe]

We'll notify you when [Feature] is available again.
We apologize for any inconvenience.

[Name]
[Title]
```

### Gradual Rollback Strategy

```
If issues detected but not critical:

Phase 1 (immediate):
├── Pause new user exposure
└── Current users unaffected

Phase 2 (if issues persist):
├── Reduce to 50% of users
└── Monitor for 30 minutes

Phase 3 (if no improvement):
├── Reduce to 10% of users
└── Monitor for 30 minutes

Phase 4 (if still problematic):
├── Full rollback
└── Root cause analysis

Benefits:
- Minimizes customer disruption
- Provides debugging opportunity
- Maintains some launch momentum
```

### Relaunch Protocol

```markdown
## Relaunch Checklist: [Feature]

### Before Scheduling Relaunch
□ Root cause identified and documented
□ Fix implemented and code-reviewed
□ Fix verified in staging environment
□ Additional test cases added for failure scenario
□ Rollback tested again

### Relaunch Communication
□ Internal teams notified of new date
□ Customer communication drafted (if needed)
□ Press/analyst update (if covered)
□ Sales re-enabled with update

### Relaunch Execution
□ Same runbook with additional monitoring
□ Lower thresholds for first 24 hours
□ Extended war room hours
□ Faster escalation paths
```

### Anti-Patterns

- **No rollback plan** — "We'll figure it out if we need to"
- **Untested rollback** — Script that fails when needed
- **Unclear authority** — Debate during crisis
- **No feature flags** — Rollback requires full deployment
- **No templates** — Writing communications during incident
- **Optimism bias** — "It won't happen to us"
- **Rollback shame** — Treating rollback as failure vs. professionalism
- **No relaunch plan** — Rollback becomes permanent
