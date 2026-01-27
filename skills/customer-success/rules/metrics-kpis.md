---
title: Success Metrics & KPIs
impact: CRITICAL
tags: metrics, nrr, grr, nps, csat, ces, health-score, kpis
---

## Success Metrics & KPIs

**Impact: CRITICAL**

You can't manage what you don't measure. But measuring the wrong things — or too many things — is worse than measuring nothing. CS metrics should drive action, not just dashboards.

### The Metrics Hierarchy

```
┌─────────────────────────────────────────────────────────────────┐
│                    BUSINESS OUTCOMES                             │
│  ════════════════════════════════════════════════════════════   │
│  NRR, GRR, Logo Retention, Revenue Churn                        │
│  → Lagging indicators, board-level, owned by CS leadership      │
├─────────────────────────────────────────────────────────────────┤
│                   LEADING INDICATORS                             │
│  ════════════════════════════════════════════════════════════   │
│  Health Score, Adoption Rate, NPS, Time-to-Value                │
│  → Predictive, operational, owned by CS ops                     │
├─────────────────────────────────────────────────────────────────┤
│                    ACTIVITY METRICS                              │
│  ════════════════════════════════════════════════════════════   │
│  Touchpoints, QBRs completed, Success plans created             │
│  → Input metrics, individual, owned by CSMs                     │
└─────────────────────────────────────────────────────────────────┘
```

### Core CS Metrics

#### Net Revenue Retention (NRR)

```
         Starting MRR + Expansion - Contraction - Churn
NRR = ──────────────────────────────────────────────────── × 100
                        Starting MRR

Example:
  Starting MRR: $1,000,000
  Expansion: $150,000
  Contraction: $30,000
  Churn: $50,000

  NRR = ($1,000,000 + $150,000 - $30,000 - $50,000) / $1,000,000
  NRR = $1,070,000 / $1,000,000 = 107%
```

| NRR | Assessment | Implication |
|-----|------------|-------------|
| <90% | Critical | Leaky bucket, growth impossible |
| 90-100% | Below average | Treading water |
| 100-110% | Good | Sustainable growth |
| 110-120% | Great | Strong expansion motion |
| >120% | Excellent | World-class, enterprise-grade |

#### Gross Revenue Retention (GRR)

```
         Starting MRR - Contraction - Churn
GRR = ────────────────────────────────────── × 100
                 Starting MRR

Example:
  Starting MRR: $1,000,000
  Contraction: $30,000
  Churn: $50,000

  GRR = ($1,000,000 - $30,000 - $50,000) / $1,000,000
  GRR = $920,000 / $1,000,000 = 92%
```

| GRR | Assessment | Benchmark |
|-----|------------|-----------|
| <80% | Critical | Serious retention issues |
| 80-85% | Below average | Typical SMB |
| 85-90% | Average | Mid-market standard |
| 90-95% | Good | Strong retention |
| >95% | Excellent | Enterprise-grade |

#### Customer Health Score

```
Health Score = Σ (Component × Weight)

Typical components:
┌─────────────────────────────────────────────────────────┐
│ Component          │ Weight │ Inputs                    │
├────────────────────┼────────┼───────────────────────────┤
│ Product Usage      │ 30%    │ DAU/MAU, feature adoption │
│ Engagement         │ 25%    │ Logins, sessions, depth   │
│ Relationship       │ 20%    │ NPS, CSM sentiment        │
│ Support            │ 15%    │ Tickets, resolution, CSAT │
│ Growth Signals     │ 10%    │ User adds, usage growth   │
└─────────────────────────────────────────────────────────┘
```

| Health Score | Status | Action |
|--------------|--------|--------|
| 80-100 | Healthy | Expansion focus |
| 60-79 | Stable | Monitor, optimize |
| 40-59 | At-risk | Proactive intervention |
| 20-39 | Critical | Executive escalation |
| 0-19 | Emergency | All-hands save attempt |

### Satisfaction Metrics

#### Net Promoter Score (NPS)

```
"How likely are you to recommend [product] to a colleague?"
Scale: 0-10

Promoters (9-10) - Detractors (0-6) = NPS
                    Total Responses

Example:
  100 responses: 50 promoters, 30 passives, 20 detractors
  NPS = (50 - 20) / 100 = 30
```

| NPS | Assessment | Industry Context |
|-----|------------|------------------|
| <0 | Critical | More detractors than promoters |
| 0-30 | Below average | Room for improvement |
| 30-50 | Good | Solid customer satisfaction |
| 50-70 | Great | Strong advocacy potential |
| >70 | Excellent | World-class, rare |

#### Customer Satisfaction Score (CSAT)

```
"How satisfied are you with [interaction/product]?"
Scale: 1-5 or 1-7

CSAT = (Satisfied responses / Total responses) × 100
"Satisfied" typically = 4-5 on 5-point scale
```

| CSAT | Assessment |
|------|------------|
| <70% | Poor |
| 70-80% | Below average |
| 80-90% | Good |
| >90% | Excellent |

#### Customer Effort Score (CES)

```
"How easy was it to [complete task/resolve issue]?"
Scale: 1-7 (1 = very easy, 7 = very difficult)

Lower is better.
```

| CES | Assessment |
|-----|------------|
| >5 | High friction, risk |
| 3-5 | Average effort |
| <3 | Low effort, good |

### Good Metrics Practice

```
✓ Focus on outcomes, not activities
  → NRR matters, calls logged doesn't
  → Health score matters, touchpoints don't (directly)

✓ Lead with leading indicators
  → Health score predicts churn
  → Don't wait for churn to measure retention

✓ Segment metrics
  → Enterprise NRR vs SMB NRR
  → Different benchmarks, different targets

✓ Tie to compensation
  → What gets measured gets managed
  → What gets compensated gets prioritized

✓ Automate collection
  → Manual metrics don't get updated
  → Integrate product, CRM, CS platform

✓ Review regularly
  → Weekly: health scores, at-risk accounts
  → Monthly: retention forecasts, segment performance
  → Quarterly: NRR/GRR trends, NPS analysis
```

### Bad Metrics Practice

```
✗ Activity metrics as primary
  → "CSMs logged 500 calls this month"
  → Means nothing about customer outcomes

✗ Vanity metrics
  → "95% of customers attended onboarding"
  → But only 40% activated

✗ Too many metrics
  → 50 KPIs means nothing is a priority
  → Focus on 5-7 that matter

✗ Manual data
  → Spreadsheet health scores
  → Always stale, inconsistent

✗ No segmentation
  → "Our NRR is 95%"
  → But SMB is 80% and Enterprise is 115%

✗ Lagging-only
  → Only know churn after it happens
  → No early warning system
```

### Metrics by Role

| Role | Primary Metrics | Secondary Metrics |
|------|-----------------|-------------------|
| **CCO/VP CS** | NRR, GRR, Logo Retention | NPS, Cost-to-serve |
| **CS Director** | Segment NRR, Renewal Rate | Health distribution, Expansion rate |
| **CS Ops** | Health Score accuracy, Automation efficiency | Process compliance |
| **CSM** | Book NRR, Health Scores | QBR completion, Time-to-value |
| **Onboarding** | Time-to-value, Activation rate | Onboarding NPS |
| **Renewals** | Renewal rate, Forecast accuracy | Early renewal rate |

### Metrics Dashboard Template

```
┌─────────────────────────────────────────────────────────────────┐
│                    CS EXECUTIVE DASHBOARD                        │
├─────────────────────────────────────────────────────────────────┤
│ BUSINESS OUTCOMES (Trailing 12 months)                          │
│ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐│
│ │ NRR: 112%   │ │ GRR: 93%    │ │ Logo: 89%   │ │ NPS: 42     ││
│ │ ▲ +3% QoQ   │ │ ▲ +1% QoQ   │ │ ═ flat      │ │ ▲ +5 QoQ    ││
│ └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘│
├─────────────────────────────────────────────────────────────────┤
│ LEADING INDICATORS                                               │
│ Health Distribution:    │ At-Risk Accounts:                      │
│ ████████████ Healthy 65% │ 12 accounts ($450k ARR)               │
│ ██████ Stable 20%       │ ▼ -3 from last month                   │
│ ███ At-risk 10%         │                                        │
│ █ Critical 5%           │                                        │
├─────────────────────────────────────────────────────────────────┤
│ THIS QUARTER                                                     │
│ Renewals due: $2.1M     │ Forecast: $1.95M (93%)                │
│ Expansion pipeline: $400k │ Expected close: $280k                │
└─────────────────────────────────────────────────────────────────┘
```

### Metric Calculation Frequencies

| Metric | Calculation | Review |
|--------|-------------|--------|
| **Health Score** | Real-time / Daily | Weekly |
| **NPS** | Survey-based (ongoing) | Monthly |
| **CSAT/CES** | Post-interaction | Weekly |
| **NRR/GRR** | Monthly calculation | Monthly, QBR |
| **Renewal forecast** | Weekly update | Weekly |
| **Time-to-value** | Per customer | Monthly aggregate |

### Building a Health Score

#### Step 1: Define Components
```
Product Usage (30%)
├── Login frequency (10%)
├── Feature breadth (10%)
└── Usage depth (10%)

Engagement (25%)
├── Sessions per user (10%)
├── Time in product (10%)
└── Active users % (5%)

Relationship (20%)
├── NPS score (10%)
├── CSM sentiment (5%)
└── Executive engagement (5%)

Support (15%)
├── Ticket volume trend (5%)
├── Ticket sentiment (5%)
└── Resolution satisfaction (5%)

Growth (10%)
├── User growth (5%)
└── Usage growth (5%)
```

#### Step 2: Define Scoring
```
For each component, score 0-100:

Login frequency example:
  0-1 logins/month: 20
  2-4 logins/month: 40
  5-10 logins/month: 60
  11-20 logins/month: 80
  20+ logins/month: 100
```

#### Step 3: Validate Correlation
```
Test health score against actual churn:
  → Churned customers should have had low scores
  → Retained customers should have had high scores
  → Adjust weights if correlation is weak
```

### Forecasting Renewals

```
Renewal Forecast = Σ (Renewal ARR × Probability)

Probability by health:
  Health 80-100: 95% probability
  Health 60-79: 85% probability
  Health 40-59: 60% probability
  Health 20-39: 30% probability
  Health 0-19: 10% probability

Example:
  Customer A: $100k ARR, Health 85 → $95k expected
  Customer B: $50k ARR, Health 45 → $30k expected
  Customer C: $75k ARR, Health 25 → $22.5k expected

  Total due: $225k
  Forecast: $147.5k (65.5%)
```

### Anti-Patterns

- **Measuring activities, not outcomes** — Calls logged ≠ value delivered
- **Ignoring leading indicators** — Churn is lagging, health is leading
- **One metric to rule them all** — NRR alone misses important signals
- **No segmentation** — Aggregate metrics hide segment problems
- **Manual data collection** — Ensures stale, unreliable metrics
- **Vanity metrics in board decks** — "Logos retained" when revenue churning
- **No action thresholds** — Health score exists but no one acts on red
- **Inconsistent definitions** — Every team calculates NRR differently
