---
title: Post-Launch Monitoring
impact: HIGH
tags: postlaunch, monitoring, metrics, operations
---

## Post-Launch Monitoring

**Impact: HIGH**

The launch isn't over when it ships. Systematic monitoring catches issues early and validates success.

### Monitoring Phases

| Phase | Duration | Focus | Cadence |
|-------|----------|-------|---------|
| **Hypercare** | Days 1-3 | Stability, critical issues | Continuous |
| **Stabilization** | Days 4-14 | Adoption, edge cases | Daily |
| **Steady State** | Days 15-30 | Trends, optimization | Weekly |
| **Long-term** | Day 30+ | Business impact | Monthly |

### Hypercare Dashboard

```
POST-LAUNCH HYPERCARE DASHBOARD
═══════════════════════════════

System Health
├── Error Rate:     0.03% [✓] (threshold: 0.1%)
├── Latency p95:    145ms [✓] (threshold: 200ms)
├── Availability:   100%  [✓] (threshold: 99.9%)
└── Queue Depth:    12    [✓] (threshold: 1000)

Adoption (T+24 hours)
├── Feature Views:  2,847
├── Feature Usage:  1,203 (42% activation)
├── Unique Users:   891
└── Target:         500   [✓] EXCEEDED

Quality
├── P0 Incidents:   0     [✓]
├── P1 Incidents:   0     [✓]
├── Bug Reports:    7     [!] (investigating 2)
└── Rollbacks:      0     [✓]

Support
├── Tickets (feature):    23
├── Avg Response Time:    12 min [✓]
├── Escalations:          1
└── CSAT:                 4.2/5 [✓]

Sentiment
├── Social Mentions:      47
├── Positive:            38 (81%)
├── Neutral:             7  (15%)
└── Negative:            2  (4%)
```

### Alert Configuration

| Metric | Warning | Critical | Action |
|--------|---------|----------|--------|
| Error rate | > 0.5% | > 1% | Page on-call |
| Latency p95 | > 300ms | > 500ms | Page on-call |
| Feature errors | > 10/hour | > 50/hour | Page on-call |
| Support volume | > 3x normal | > 5x normal | Alert PM |
| Negative social | > 5 mentions | > 10 mentions | Alert PMM |

### Good Example: Effective Monitoring

```markdown
## Post-Launch Monitoring Report: Enterprise SSO
### Day 3 Summary

**Executive Summary:**
SSO launch performing above expectations. No critical issues.
Adoption 40% ahead of target. Recommend moving to stabilization phase.

**System Health:**
| Metric | Day 1 | Day 2 | Day 3 | Target |
|--------|-------|-------|-------|--------|
| Error rate | 0.05% | 0.03% | 0.02% | < 0.1% |
| Latency | 180ms | 165ms | 155ms | < 200ms |
| Uptime | 100% | 100% | 100% | 99.9% |

**Adoption Metrics:**
| Metric | Day 1 | Day 2 | Day 3 | Target |
|--------|-------|-------|-------|--------|
| SSO setups | 89 | 67 | 54 | 50/day |
| Active SSO users | 2,340 | 4,120 | 5,890 | 3,000 |
| Setup success rate | 94% | 96% | 97% | > 90% |

**Issues Identified:**
1. Minor: Setup wizard confusing for Azure AD (12 tickets)
   - Action: UX improvement scheduled for next sprint
   - Workaround: Updated documentation

2. Edge case: SCIM sync delay for > 500 user orgs
   - Action: Engineering investigating
   - Impact: 3 customers, all contacted

**Support Analysis:**
- Total tickets: 47 (expected ~60)
- Most common: "How do I set up?" (18) - Resolved with docs link
- Top issue: Azure AD confusion (12) - Action item above

**Recommendation:** Exit hypercare, enter stabilization phase
```

### Bad Example: No Monitoring

```markdown
## What Happened: Reporting 2.0 Launch

**Week 1:**
- PM: "Launch went great!"
- No dashboard, no tracking

**Week 2:**
- Support: "We're getting a lot of tickets about reports"
- PM: "How many?"
- Support: "I don't know, a lot"

**Week 3:**
- Exec: "Customer X says reports are broken"
- PM: "First I'm hearing of this"
- Discovered: 15% error rate for 2 weeks
- Discovered: 340 support tickets about feature
- Discovered: 3 enterprise customers considering churn

**Root Cause:**
- No error monitoring configured
- No feature-specific dashboards
- No support ticket categorization
- No regular review cadence
```

### Monitoring Checklist by Role

**Engineering:**
```
Daily (Hypercare):
□ Review error rate trends
□ Check latency percentiles
□ Verify no P0/P1 incidents
□ Review bug reports
□ Check infrastructure capacity

Weekly (Stabilization):
□ Performance trend analysis
□ Edge case identification
□ Technical debt assessment
□ Scaling projections
```

**Product:**
```
Daily (Hypercare):
□ Review adoption metrics
□ Check support trends
□ Triage bug reports
□ Customer feedback review

Weekly (Stabilization):
□ Adoption funnel analysis
□ Success criteria assessment
□ Feature iteration planning
□ Stakeholder update
```

**Marketing:**
```
Daily (Hypercare):
□ Social sentiment monitoring
□ Press coverage tracking
□ Campaign performance

Weekly (Stabilization):
□ Content performance analysis
□ Lead attribution review
□ Campaign optimization
```

### Success Criteria Tracking

```markdown
## Success Criteria Dashboard: SSO Launch

### Adoption (Target: Week 4)
| Metric | Target | Week 1 | Week 2 | Week 3 | Week 4 |
|--------|--------|--------|--------|--------|--------|
| Setups | 200 | 210 ✓ | 285 ✓ | 340 ✓ | 390 ✓ |
| Active | 5,000 | 3,800 | 6,200 ✓ | 8,100 ✓ | 9,500 ✓ |
| Activation % | 30% | 25% | 32% ✓ | 35% ✓ | 38% ✓ |

### Quality (Target: Ongoing)
| Metric | Target | Week 1 | Week 2 | Week 3 | Week 4 |
|--------|--------|--------|--------|--------|--------|
| Error rate | < 0.1% | 0.03% ✓ | 0.02% ✓ | 0.02% ✓ | 0.01% ✓ |
| P0 incidents | 0 | 0 ✓ | 0 ✓ | 0 ✓ | 0 ✓ |
| Setup NPS | > 50 | 52 ✓ | 58 ✓ | 61 ✓ | 64 ✓ |

### Business (Target: Quarter)
| Metric | Target | Month 1 | Month 2 | Month 3 |
|--------|--------|---------|---------|---------|
| Pipeline | $500K | $180K | $380K | $620K ✓ |
| Won deals | 5 | 2 | 4 | 7 ✓ |

**Overall Status: ON TRACK FOR SUCCESS**
```

### Escalation Triggers

| Signal | Trigger | Escalate To | Action |
|--------|---------|-------------|--------|
| Error rate | > 1% sustained | Eng Lead | Incident response |
| Adoption | < 50% of target at midpoint | PM + PMM | Adoption campaign |
| Support volume | > 5x normal, sustained | Support Lead + PM | Triage + fix |
| Churn signal | Any customer citing feature | CS Lead + PM | Customer outreach |
| Negative press | Major outlet | Comms Lead | Response plan |

### Transition Criteria

**Hypercare → Stabilization:**
```
□ Zero P0/P1 incidents for 48 hours
□ Error rate < threshold for 48 hours
□ Support volume trending down
□ No unresolved critical bugs
```

**Stabilization → Steady State:**
```
□ No incidents for 2 weeks
□ Support volume at normal levels
□ Adoption tracking to targets
□ All launch bugs resolved or scheduled
```

### Anti-Patterns

- **No monitoring** — Assuming it works until someone complains
- **Vanity dashboards** — Tracking page views, not activation
- **Alert fatigue** — So many alerts, real issues ignored
- **No thresholds** — Looking at numbers without targets
- **PM absence** — Engineering monitors alone
- **Snapshot only** — Checking once, not trending
- **No support integration** — Tickets not linked to feature
- **Too short hypercare** — Ending monitoring after 24 hours
