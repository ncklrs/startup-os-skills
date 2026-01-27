---
title: Product Metrics and OKRs
impact: CRITICAL
tags: metrics, okrs, kpis, measurement, outcomes
---

## Product Metrics and OKRs

**Impact: CRITICAL**

What you measure defines what you build. Great PMs obsess over outcomes, not outputs.

### Metrics Hierarchy

```
┌─────────────────────────────────────────────────────────────────┐
│                    NORTH STAR METRIC                            │
│              (One metric that captures value)                   │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│    ┌──────────────┐  ┌──────────────┐  ┌──────────────┐        │
│    │   INPUT      │  │   INPUT      │  │   INPUT      │        │
│    │   METRIC 1   │  │   METRIC 2   │  │   METRIC 3   │        │
│    └──────────────┘  └──────────────┘  └──────────────┘        │
│                                                                 │
│    ┌──────────────┐  ┌──────────────┐  ┌──────────────┐        │
│    │   GUARDRAIL  │  │   GUARDRAIL  │  │   GUARDRAIL  │        │
│    │   METRIC 1   │  │   METRIC 2   │  │   METRIC 3   │        │
│    └──────────────┘  └──────────────┘  └──────────────┘        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### North Star Metric Examples

| Company Type | North Star | Why |
|--------------|------------|-----|
| **SaaS** | Weekly Active Users | Reflects ongoing value delivery |
| **E-commerce** | Revenue per User | Captures conversion + AOV |
| **Marketplace** | Transactions completed | Value exchange happening |
| **Media** | Time spent | Engagement depth |
| **B2B** | Seats activated | Expansion within accounts |
| **Freemium** | Paid conversion rate | Business model validation |

### Input vs Output vs Outcome Metrics

| Type | Definition | Example | Use |
|------|------------|---------|-----|
| **Input** | Activities/effort | Features shipped, experiments run | Team activity |
| **Output** | Direct results | Signups, page views | Feature success |
| **Outcome** | Business impact | Revenue, retention, NPS | Goal achievement |

**Always optimize for outcomes, not outputs.**

### AARRR Pirate Metrics Framework

| Stage | Definition | Key Metrics |
|-------|------------|-------------|
| **Acquisition** | Users discover product | Visitors, signups, channel performance |
| **Activation** | Users experience value | Activation rate, time-to-value, onboarding completion |
| **Retention** | Users return | DAU/MAU, retention curves, churn rate |
| **Revenue** | Users pay | Conversion rate, ARPU, LTV |
| **Referral** | Users recommend | NPS, viral coefficient, referral rate |

### Good OKRs Example

```markdown
## Q1 2024 OKRs - Product Team

### Objective 1: Dramatically improve new user activation
**Why:** 60% of users never experience core value; biggest growth lever

**Key Results:**
- KR1: Increase activation rate from 23% to 35%
  - Measurement: Users completing first workflow within 7 days
  - Current: 23% | Target: 35%

- KR2: Reduce time-to-first-value from 3 days to 1 day
  - Measurement: Median time to first successful workflow
  - Current: 72 hours | Target: 24 hours

- KR3: Achieve 50+ NPS for users in first 30 days
  - Measurement: NPS survey at day 30
  - Current: 32 | Target: 50

**Initiatives:**
- Onboarding flow redesign
- Template library expansion
- In-app guidance system

**Guardrails:**
- Support ticket volume: maintain < 5% increase
- Infrastructure cost: no increase > 10%
```

### Bad OKRs Example

```markdown
## Q1 OKRs

### Objective 1: Ship new features
**Key Results:**
- Ship dark mode
- Launch mobile app
- Add 10 integrations
- Redesign dashboard

### Objective 2: Make customers happy
**Key Results:**
- Get more feedback
- Fix bugs
- Improve performance
```

**Why this fails:**
- Output-focused, not outcome-focused
- No measurable targets
- No baseline or current state
- No connection to business value
- No guardrails

### OKR Writing Guidelines

**Good Objective:**
- Qualitative and inspirational
- Time-bound (quarterly)
- Ambitious but achievable
- Team-aligned

**Good Key Results:**
- Quantitative and measurable
- Outcome-focused (not output)
- 3-5 per objective
- Include baseline and target
- Challenging but possible (70% confidence)

### Metric Definition Template

```markdown
## Metric: Activation Rate

### Definition
Percentage of new signups who complete their first successful
workflow within 7 days of registration.

### Formula
(Users with completed workflow in first 7 days / Total new signups) × 100

### Data Source
- Numerator: events.workflow_completed WHERE days_since_signup <= 7
- Denominator: users.created_at in period

### Segmentation
- By signup source (organic, paid, referral)
- By plan type (free, trial, paid)
- By company size (SMB, mid-market, enterprise)

### Cadence
- Reported: Weekly
- Reviewed: Monthly

### Owner
Product Manager - Growth

### Targets
| Period | Target | Stretch |
|--------|--------|---------|
| Q1 2024 | 35% | 40% |
| Q2 2024 | 42% | 48% |

### Related Metrics
- Time-to-first-value (leading)
- 30-day retention (lagging)
- Onboarding completion (input)
```

### Metrics Review Meeting Agenda

```markdown
## Weekly Metrics Review - [Date]

### Attendees
Product, Engineering Lead, Data

### Agenda

#### 1. North Star Check (5 min)
- Current: [value]
- Trend: [up/down/flat]
- vs Target: [ahead/behind/on track]

#### 2. Key Result Progress (15 min)
| KR | Current | Target | Status |
|----|---------|--------|--------|
| Activation rate | 28% | 35% | On track |
| Time-to-value | 2 days | 1 day | At risk |
| NPS (new users) | 41 | 50 | On track |

#### 3. Guardrail Check (5 min)
| Guardrail | Status | Notes |
|-----------|--------|-------|
| Support volume | Green | +2% |
| Error rate | Green | 0.1% |
| Infrastructure cost | Yellow | +8% |

#### 4. Experiment Results (10 min)
- [Experiment A]: +3% activation, shipping
- [Experiment B]: No significant change, not shipping

#### 5. Insights & Actions (10 min)
- Key insight: [Finding]
- Action: [What we're doing about it]

### Decisions Made
- [Decision 1]
- [Decision 2]

### Next Week Focus
- [Priority 1]
- [Priority 2]
```

### Common Metric Pitfalls

| Pitfall | Description | Better Approach |
|---------|-------------|-----------------|
| **Vanity metrics** | Looks good but doesn't drive business | Focus on actionable metrics |
| **Undefined metrics** | Different teams measure differently | Document precise definitions |
| **Too many metrics** | Dashboard overload | Focus on 3-5 key metrics |
| **No baselines** | Can't tell if improving | Always measure current state |
| **Lagging only** | Only see problems after the fact | Balance leading + lagging |
| **Gaming** | Optimizing metric at expense of value | Add guardrails |

### Anti-Patterns

- **Feature counting** — Measuring what you shipped, not impact
- **Metric theater** — Beautiful dashboards nobody uses
- **Annual OKRs** — Too long to learn and adapt
- **Sandbagging** — Setting easy targets to "hit" OKRs
- **Set and forget** — Not reviewing regularly
- **Too many KRs** — 10 key results per objective
- **No accountability** — OKRs without owners
- **Input KRs** — "Ship 5 features" as a key result
