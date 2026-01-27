---
title: Launch Success Criteria
impact: CRITICAL
tags: planning, metrics, success, measurement
---

## Launch Success Criteria

**Impact: CRITICAL**

Define success before launch, not after. Post-hoc success criteria is rationalization, not measurement.

### Success Criteria Framework

Every launch needs metrics across four dimensions:

| Dimension | What It Measures | When to Measure | Owner |
|-----------|-----------------|-----------------|-------|
| **Adoption** | Are users using it? | Day 1, Week 1, Month 1 | Product |
| **Quality** | Is it working well? | Real-time, Daily | Engineering |
| **Business** | Is it driving results? | Month 1, Quarter 1 | Product/Sales |
| **Sentiment** | Do users like it? | Week 1, Month 1 | Product/Support |

### Adoption Metrics by Tier

| Tier | Day 1 | Week 1 | Month 1 |
|------|-------|--------|---------|
| **Tier 1** | 5% of users try | 15% activated | 30% retained |
| **Tier 2** | 3% of segment tries | 10% activated | 25% retained |
| **Tier 3** | 1% of users try | 5% activated | 20% retained |
| **Tier 4** | N/A | Usage baseline | No regression |

### Quality Metrics (All Tiers)

```
Error Rate:        < 0.1% of requests
Latency:          < 200ms p95 (or no regression)
Availability:      99.9% uptime
Incidents:         Zero P0/P1 in first 48 hours
Rollback:          Zero rollbacks required
```

### Good Example: Comprehensive Success Criteria

```markdown
## Success Criteria: Enterprise SSO Launch

### Adoption (Product owns)
| Metric | Target | Measurement |
|--------|--------|-------------|
| Enterprise accounts enabling SSO | 25% in 30 days | Product analytics |
| Time to SSO setup | < 30 minutes | Instrumentation |
| SSO login rate post-setup | > 90% | Auth logs |

### Quality (Engineering owns)
| Metric | Target | Measurement |
|--------|--------|-------------|
| SSO auth latency | < 500ms p95 | APM |
| Auth error rate | < 0.01% | Error tracking |
| Availability | 99.99% | Uptime monitoring |

### Business (Sales/Product owns)
| Metric | Target | Measurement |
|--------|--------|-------------|
| Pipeline influenced | $500K in 90 days | CRM attribution |
| Enterprise close rate | +5% improvement | Sales analytics |
| Competitive win rate | +10% vs SSO objection | Win/loss analysis |

### Sentiment (Product/Support owns)
| Metric | Target | Measurement |
|--------|--------|-------------|
| Setup NPS | > 50 | Post-setup survey |
| Support tickets | < 10% of enablements | Zendesk |
| Admin feedback | Qualitative positive | Customer calls |
```

### Bad Example: Vague Success Criteria

```markdown
## Success Criteria: New Dashboard

- Users should like it
- It should be fast
- We want lots of adoption
- Good feedback from customers

**Why This Fails:**
- No specific numbers
- No timeline for measurement
- No owners assigned
- No measurement method defined
- "Lots" and "good" are not metrics
```

### The SMART Criteria Test

Every metric should pass SMART:

| Criteria | Question | Example |
|----------|----------|---------|
| **Specific** | What exactly? | "SSO activation rate" not "adoption" |
| **Measurable** | How do we count? | "Product analytics event" |
| **Achievable** | Is it realistic? | Based on comparable launches |
| **Relevant** | Does it matter? | Tied to business outcome |
| **Time-bound** | By when? | "30 days post-launch" |

### Baseline Requirements

Before setting targets, establish baselines:

```
Current State Analysis:
┌─────────────────────────────────────────┐
│ Comparable Feature Launch (6 months ago) │
│ - Day 1 adoption: 2%                     │
│ - Week 1 activation: 8%                  │
│ - Month 1 retention: 18%                 │
│                                          │
│ Target for This Launch:                  │
│ - Day 1 adoption: 3% (+50%)              │
│ - Week 1 activation: 10% (+25%)          │
│ - Month 1 retention: 25% (+38%)          │
└─────────────────────────────────────────┘
```

### Success Criteria Sign-off

| Stakeholder | Signs Off On | Before |
|-------------|--------------|--------|
| Product Lead | All metrics & targets | Launch brief approval |
| Engineering Lead | Quality metrics & feasibility | T-4 weeks |
| Marketing Lead | Campaign success metrics | T-4 weeks |
| Sales Lead | Business metrics & attribution | T-4 weeks |
| Executive Sponsor | Overall success bar | Go/no-go |

### Post-Launch Success Review Template

```markdown
## Launch Success Review: [Feature Name]

**Launch Date:** [Date]
**Review Date:** [Date]

### Adoption Results
| Metric | Target | Actual | Status |
|--------|--------|--------|--------|
| [Metric] | [Target] | [Actual] | [Met/Missed] |

### Quality Results
| Metric | Target | Actual | Status |
|--------|--------|--------|--------|

### Business Results
| Metric | Target | Actual | Status |
|--------|--------|--------|--------|

### Sentiment Results
| Metric | Target | Actual | Status |
|--------|--------|--------|--------|

### Overall Assessment: [SUCCESS / PARTIAL / MISSED]

### Key Learnings:
1. [Learning]
2. [Learning]

### Follow-up Actions:
1. [Action] - Owner: [Name] - Due: [Date]
```

### Anti-Patterns

- **Post-launch metrics** — Deciding what success looks like after you know results
- **Vanity metrics only** — Page views without activation
- **No baseline** — Targets with no reference point
- **Moving goalposts** — Changing targets when you're missing them
- **Single dimension** — Measuring adoption but not quality
- **No owner** — Metrics without accountability
- **Unmeasurable targets** — "Improved customer satisfaction"
