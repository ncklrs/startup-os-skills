---
title: Health Score Design & Weighting
impact: CRITICAL
tags: health-score, weighting, methodology, scoring-algorithm
---

## Health Score Design & Weighting

**Impact: CRITICAL**

A well-designed health score predicts customer outcomes 60-90 days before they happen. Poor health scores are vanity metrics that provide false confidence while customers silently churn.

### The Health Score Equation

```
Health Score = Σ (Component Score × Weight)

Where:
- Each component is normalized to 0-100
- Weights sum to 100%
- Final score ranges 0-100
```

### Component Selection Criteria

| Criterion | Question | Example |
|-----------|----------|---------|
| **Predictive** | Does this signal future outcomes? | Usage decline predicts churn |
| **Measurable** | Can we reliably track this? | Login frequency vs. "satisfaction" |
| **Actionable** | Can we influence this? | Feature adoption (yes) vs. company size (no) |
| **Timely** | Do we get the signal early enough? | Leading indicators only |
| **Available** | Do we have access to this data? | CRM data vs. internal discussions |

### Standard Health Score Components

| Component | Typical Weight | Sub-Metrics |
|-----------|----------------|-------------|
| **Product Usage** | 30-40% | DAU/MAU, feature breadth, depth, frequency |
| **Engagement** | 20-25% | NPS, CSM touchpoints, email responsiveness |
| **Growth Signals** | 15-20% | Seat expansion, usage trend, contract growth |
| **Support Health** | 15-20% | Ticket volume, sentiment, resolution satisfaction |
| **Financial Health** | 5-10% | Payment history, contract terms, billing issues |

### Weight Assignment by Business Model

| Business Model | Usage | Engagement | Growth | Support | Financial |
|----------------|-------|------------|--------|---------|-----------|
| **Self-serve SaaS** | 45% | 15% | 20% | 15% | 5% |
| **Enterprise SaaS** | 30% | 30% | 15% | 15% | 10% |
| **Usage-based** | 50% | 15% | 20% | 10% | 5% |
| **High-touch services** | 20% | 40% | 15% | 20% | 5% |

### Good Health Score Design

```
Health Score v2.0 - Enterprise Accounts

Component: Product Usage (35%)
├── DAU/MAU ratio (10%)
│   └── 30-day rolling average
├── Feature adoption score (10%)
│   └── % of key features used
├── Usage depth (10%)
│   └── Actions per session
└── Core workflow completion (5%)
    └── % completing primary use case

Component: Engagement (25%)
├── Relationship NPS (10%)
│   └── Most recent score
├── CSM touchpoints (8%)
│   └── Meetings held vs. scheduled
└── Communication responsiveness (7%)
    └── Email response rate

Component: Growth Signals (20%)
├── Seat expansion trend (8%)
│   └── 90-day user growth rate
├── Usage expansion trend (7%)
│   └── 90-day consumption growth
└── Contract expansion (5%)
    └── Any expansion in last year

Component: Support Health (20%)
├── Ticket sentiment (8%)
│   └── AI-analyzed support conversations
├── Resolution satisfaction (7%)
│   └── Post-ticket CSAT
└── Escalation frequency (5%)
    └── Escalations per month

Scoring:
- All sub-metrics normalized to 0-100
- Component score = weighted average of sub-metrics
- Final score = weighted sum of components
```

### Bad Health Score Design

```
Health Score v1.0 (Problems Identified)

Components:
├── Product Usage (70%)          ← Over-weighted single category
│   └── Total logins             ← Vanity metric
│
├── Support Tickets (15%)        ← Direction unclear
│   └── Total tickets opened     ← More tickets = lower score?
│
└── Contract Value (15%)         ← Not predictive
    └── ARR                      ← Bigger customers ≠ healthier

Problems:
✗ Over-reliance on single category
✗ Logins don't measure value
✗ Tickets could be good (engaged) or bad (frustrated)
✗ ARR doesn't predict retention
✗ No engagement or relationship signals
✗ No leading indicators
```

### Scoring Algorithm Examples

**Linear Scoring:**
```
Score = (Actual Value / Target Value) × 100
Cap at 100, floor at 0

Example: DAU/MAU
Target: 40%
Actual: 32%
Score: (32/40) × 100 = 80
```

**Threshold-Based Scoring:**
```
If DAU/MAU >= 50%: Score = 100
If DAU/MAU >= 40%: Score = 80
If DAU/MAU >= 30%: Score = 60
If DAU/MAU >= 20%: Score = 40
If DAU/MAU >= 10%: Score = 20
If DAU/MAU < 10%:  Score = 0
```

**Trend-Adjusted Scoring:**
```
Base Score = Current metric score
Trend Factor = (Current - 30 days ago) / 30 days ago
Adjusted Score = Base Score × (1 + Trend Factor × 0.2)

Example:
Base Score: 70
Usage up 15%: 70 × 1.03 = 72.1
Usage down 15%: 70 × 0.97 = 67.9
```

### Health Score Thresholds

| Score Range | Status | Color | Action Priority |
|-------------|--------|-------|-----------------|
| 85-100 | Thriving | Green | Expansion focus |
| 70-84 | Healthy | Light Green | Monitor, optimize |
| 50-69 | Neutral | Yellow | Proactive engagement |
| 30-49 | At-Risk | Orange | Immediate intervention |
| 0-29 | Critical | Red | Executive escalation |

### Threshold Calibration Process

```
Step 1: Historical Analysis
- Pull 12+ months of health scores
- Tag customers by outcome (churned, retained, expanded)
- Plot score distribution by outcome

Step 2: Threshold Identification
- Find score ranges where outcomes diverge
- Identify clear "danger zones"
- Map to intervention capacity

Step 3: Validation
- Apply thresholds prospectively
- Track prediction accuracy
- Measure false positive/negative rates

Step 4: Refinement
- Adjust thresholds quarterly
- Segment-specific thresholds if needed
- Document rationale for changes
```

### Health Score Validation Metrics

| Metric | Target | Calculation |
|--------|--------|-------------|
| **Churn Prediction Accuracy** | >70% | Predicted churn / Actual churn |
| **False Positive Rate** | <25% | False at-risk / Total at-risk |
| **False Negative Rate** | <15% | Surprise churns / Total churns |
| **Score-Outcome Correlation** | >0.5 | Pearson correlation |
| **Segment Consistency** | Similar | Same score ≈ same outcomes |

### Segment-Specific Scoring Considerations

| Segment | Adjustment |
|---------|------------|
| **Enterprise** | Weight relationship higher, usage patterns differ |
| **SMB** | Weight product usage higher, less CSM touchpoints |
| **New customers** | Separate onboarding score, don't penalize low tenure |
| **High-growth** | Adjust for rapid seat expansion volatility |
| **Seasonal** | Normalize for expected usage patterns |

### Health Score Implementation Checklist

```
□ Component Selection
  □ Each component has clear predictive value
  □ All data sources are reliable and available
  □ Metrics are actionable (we can influence them)
  □ No duplicate signals across components

□ Weight Assignment
  □ Weights based on historical correlation analysis
  □ Weights sum to 100%
  □ No single component dominates (max 40%)
  □ Weights documented with rationale

□ Scoring Logic
  □ All sub-metrics normalized consistently (0-100)
  □ Handling for missing data defined
  □ Edge cases documented (new customers, etc.)
  □ Calculation logic peer-reviewed

□ Threshold Definition
  □ Thresholds based on outcome analysis
  □ Clear actions mapped to each threshold
  □ Thresholds validated against historical data
  □ Segment-specific adjustments if needed

□ Operational Readiness
  □ Score calculation automated
  □ Update frequency defined (daily/weekly)
  □ Alerting configured for threshold crossings
  □ Dashboard visibility for CS team

□ Ongoing Governance
  □ Quarterly calibration review scheduled
  □ Accuracy metrics tracked
  □ Feedback loop from CS team
  □ Version history maintained
```

### Anti-Patterns

- **Kitchen sink scoring** — Including every metric regardless of predictive value
- **Equal weighting** — All components at 20% without analysis
- **Binary signals** — Using yes/no when degree matters
- **Static thresholds** — Never recalibrating as business changes
- **Ignoring tenure** — New customers scored same as mature ones
- **Vanity components** — Metrics that feel important but don't predict
- **Over-fitting** — Optimizing for historical data, failing on new patterns
- **No documentation** — Scoring logic understood by one person only
