---
title: Leading vs Lagging Indicator Analysis
impact: CRITICAL
tags: leading-indicators, lagging-indicators, predictive-signals, correlation
---

## Leading vs Lagging Indicator Analysis

**Impact: CRITICAL**

By the time you see lagging indicators (churn, downgrades), it's often too late. Leading indicators give you the 60-90 day window needed to intervene effectively. The best customer success teams obsess over leading indicators.

### Indicator Classification Framework

```
Timeline to Outcome:
────────────────────────────────────────────────────────►
│                                                       │
│  LEADING           COINCIDENT         LAGGING        │
│  (60-90 days)      (30-60 days)       (0-30 days)   │
│                                                       │
│  ✓ Actionable      ~ Urgent           ✗ Historical  │
│  ✓ Predictive      ~ Confirmatory     ✗ Reactive    │
│  ✓ Proactive       ~ Responsive       ✗ Post-mortem │
│                                                       │
└───────────────────────────────────────────────────────┘
```

### Common Indicator Categories

| Category | Leading (60-90 days) | Coincident (30-60 days) | Lagging (0-30 days) |
|----------|---------------------|------------------------|---------------------|
| **Usage** | Feature adoption declining | Login frequency dropping | Account dormant |
| **Engagement** | Missed scheduled meetings | Unresponsive to outreach | No contact 60+ days |
| **Sentiment** | Support ticket tone change | NPS score drop | Cancellation request |
| **Financial** | Contract questions | Downgrade inquiry | Non-renewal notice |
| **Organizational** | Champion on LinkedIn | New stakeholder introduced | Champion departed |

### Leading Indicator Catalog

| Indicator | Signal Type | Detection Method | Action Window |
|-----------|-------------|------------------|---------------|
| DAU/MAU declining >20% | Usage | Product analytics | 90 days |
| Key feature abandonment | Usage | Event tracking | 75 days |
| Power user disengagement | Usage | User segmentation | 60 days |
| CSM meeting cancellations | Engagement | Calendar tracking | 60 days |
| Exec sponsor unresponsive | Engagement | Communication logs | 75 days |
| Support ticket sentiment shift | Sentiment | NLP analysis | 45 days |
| Renewal meeting not scheduled | Financial | CSM activity | 90 days |
| Budget/cost questions | Financial | Call transcripts | 60 days |
| Champion job change signals | Organizational | LinkedIn tracking | 90 days |
| New stakeholder evaluation | Organizational | CSM notes | 60 days |

### Good Leading Indicator Analysis

```
Indicator: Feature Adoption Decline

Definition:
- Customer using <50% of features used at peak
- Measured over rolling 30-day window
- Compared to their own historical baseline

Why It's Leading:
- Precedes churn by 75 days on average
- Indicates value not being realized
- Actionable through enablement

Detection:
- Automated daily feature usage calculation
- Alert when adoption drops below threshold
- Trend visualization in health dashboard

Correlation Analysis:
- 68% of customers with this signal churned within 120 days
- Only 12% of customers without this signal churned
- Predictive accuracy: 73%

Action Trigger:
When detected → CSM outreach within 48 hours
Goal → Feature re-enablement or use case pivot
```

### Bad Leading Indicator Analysis

```
Indicator: Low NPS Score

Problems:
✗ NPS is often coincident or lagging, not leading
✗ By the time NPS drops, issues are entrenched
✗ Quarterly surveys miss the window
✗ NPS alone lacks actionability

Better Approach:
- Track NPS trend (leading signal: declining NPS)
- Combine with other signals (NPS + usage decline)
- Use transactional NPS for faster feedback
- Look at verbatim comments for leading signals

Correlation Reality:
- Static low NPS: 45% correlation to churn
- Declining NPS trend: 72% correlation to churn
- The trend is the leading indicator, not the score
```

### Correlation Analysis Methodology

```
Step 1: Define Outcomes
- Primary: Churn (Y/N)
- Secondary: Expansion, Contraction, NRR

Step 2: Identify Candidate Signals
- List all measurable customer behaviors
- Include product, engagement, support, financial

Step 3: Time-Shift Analysis
For each signal at each lag period (30, 60, 90, 120 days):
- Calculate correlation to outcome
- Identify optimal prediction window

Step 4: Signal Ranking
- Rank by correlation strength
- Consider actionability
- Assess data availability

Step 5: Combine for Prediction
- Build composite leading indicator score
- Validate on holdout data
- Monitor ongoing accuracy
```

### Correlation Strength Benchmarks

| Correlation | Interpretation | Action |
|-------------|----------------|--------|
| >0.7 | Strong predictor | High priority signal |
| 0.5-0.7 | Moderate predictor | Include in model |
| 0.3-0.5 | Weak predictor | Combine with others |
| <0.3 | Not predictive | Exclude or investigate |

### Signal Combination Matrix

| If Signal A... | And Signal B... | Risk Level | Action |
|----------------|-----------------|------------|--------|
| Usage declining | Engagement stable | Medium | Enablement focus |
| Usage stable | Engagement declining | Medium | Relationship focus |
| Usage declining | Engagement declining | High | Executive intervention |
| Usage declining | Support tickets increasing | Critical | Immediate escalation |
| Champion active | Usage declining | Medium-High | Champion conversation |
| Champion inactive | Usage stable | Medium | Find new champion |

### Good Indicator Monitoring Dashboard

```
Leading Indicator Dashboard

┌─────────────────────────────────────────────────────────┐
│  LEADING INDICATOR ALERTS (Last 7 Days)                 │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  Critical (Action Required):                   12       │
│  ├── Usage Decline >30%                        5       │
│  ├── Champion Departure Detected               3       │
│  └── Renewal Meeting Not Scheduled             4       │
│                                                         │
│  Warning (Monitor Closely):                    28       │
│  ├── Feature Adoption Declining                12      │
│  ├── Engagement Score Down                     9       │
│  └── Support Sentiment Shift                   7       │
│                                                         │
├─────────────────────────────────────────────────────────┤
│  INDICATOR TRENDS (90-Day)                              │
│                                                         │
│  Usage Decline Alerts:     ▲ +15% vs prior period      │
│  Champion Departures:      ▼ -8% vs prior period       │
│  Engagement Drops:         ─ Flat vs prior period      │
│                                                         │
├─────────────────────────────────────────────────────────┤
│  PREDICTION ACCURACY (Last Quarter)                     │
│                                                         │
│  Churns Predicted:         42/51 (82%)                 │
│  False Positives:          15/42 (36%)                 │
│  Avg Lead Time:            67 days                     │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

### Building Your Leading Indicator Model

| Step | Action | Output |
|------|--------|--------|
| 1 | Collect 12+ months historical data | Data set |
| 2 | Tag outcomes (churn, retain, expand) | Labeled data |
| 3 | Calculate all signals at various time lags | Signal matrix |
| 4 | Run correlation analysis | Ranked signals |
| 5 | Select top 5-8 leading indicators | Indicator set |
| 6 | Define thresholds for each | Alert rules |
| 7 | Build composite score | Leading indicator score |
| 8 | Validate on holdout data | Accuracy metrics |
| 9 | Implement monitoring | Automated alerts |
| 10 | Refine quarterly | Continuous improvement |

### Action Triggers by Signal

| Signal | Threshold | Action | Owner | SLA |
|--------|-----------|--------|-------|-----|
| Usage decline | >25% MoM | CSM outreach | CSM | 48 hrs |
| Feature abandonment | Key feature unused 30+ days | Enablement call | CSM | 1 week |
| Champion departure | LinkedIn change detected | Stakeholder mapping | CSM + Manager | 24 hrs |
| NPS decline | Drop of 3+ points | Root cause analysis | CSM | 1 week |
| Support sentiment | Negative trend detected | Service review | Support Lead | 48 hrs |
| Meeting cancellation | 2+ consecutive | Manager check-in | CSM Manager | 1 week |
| Budget questions | Detected in call | Value realization review | CSM | 48 hrs |

### Indicator Validation Checklist

```
□ Predictive Power
  □ Correlation to outcome >0.5
  □ Consistent across customer segments
  □ Maintains accuracy over time
  □ Not just correlating with another signal

□ Actionability
  □ Clear intervention available
  □ Enough lead time to act (60+ days)
  □ Team has capacity to respond
  □ Success interventions documented

□ Reliability
  □ Data source is consistent
  □ Signal can be calculated automatically
  □ Missing data handling defined
  □ False positive rate acceptable (<30%)

□ Operationalization
  □ Real-time or near-real-time detection
  □ Alerts configured and routed correctly
  □ Playbook exists for each signal
  □ Feedback loop to improve model
```

### Anti-Patterns

- **Lagging indicator focus** — Tracking churn rate instead of churn predictors
- **Single indicator reliance** — One signal without confirmation
- **Ignoring signal combinations** — Missing that A + B together is critical
- **Static thresholds** — Not adjusting for segment or seasonality
- **No validation** — Using indicators without testing predictive power
- **Action-less alerts** — Signals without defined responses
- **Too many indicators** — Alert fatigue from over-monitoring
- **Ignoring false positives** — Not refining to reduce noise
