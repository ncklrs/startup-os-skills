---
title: Health Model Validation & Calibration
impact: HIGH
tags: model-validation, calibration, accuracy, continuous-improvement
---

## Health Model Validation & Calibration

**Impact: HIGH**

A health score model is only valuable if it accurately predicts outcomes. Without regular validation and calibration, models drift, accuracy degrades, and teams lose confidence. Continuous validation ensures your health scores remain actionable and trustworthy.

### The Validation Lifecycle

```
┌──────────────────────────────────────────────────────────────────┐
│                  MODEL VALIDATION LIFECYCLE                      │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│       ┌─────────┐                                                │
│       │  BUILD  │                                                │
│       └────┬────┘                                                │
│            │                                                     │
│            ▼                                                     │
│       ┌─────────┐      ┌─────────┐      ┌─────────┐            │
│       │ DEPLOY  │ ───► │ MONITOR │ ───► │ ANALYZE │            │
│       └─────────┘      └────┬────┘      └────┬────┘            │
│            ▲                │                │                  │
│            │                ▼                ▼                  │
│            │           ┌─────────┐      ┌─────────┐            │
│            └───────────│ REFINE  │ ◄─── │ CALIBRATE│            │
│                        └─────────┘      └─────────┘            │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Key Validation Metrics

| Metric | Definition | Target | Red Flag |
|--------|------------|--------|----------|
| **Churn Prediction Accuracy** | Predicted churns / Actual churns | >70% | <50% |
| **Surprise Churn Rate** | Churns with health >60 / Total churns | <20% | >35% |
| **False Positive Rate** | False at-risk / Flagged at-risk | <30% | >50% |
| **Score-Outcome Correlation** | Pearson correlation (score, outcome) | >0.5 | <0.3 |
| **Lift at 10%** | Top decile churn rate / Overall rate | >3x | <2x |
| **Score Distribution** | Spread across 0-100 range | Normal | Bimodal/Skewed |
| **Calibration Error** | Avg(Predicted prob - Actual prob) | <5% | >15% |

### Good Model Validation Report

```
Health Score Model Validation Report
Period: Q4 2024

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

EXECUTIVE SUMMARY

Model performance meets targets across key metrics.
Prediction accuracy improved 8% vs. Q3 following
feature updates. One area of concern: enterprise
segment showing higher surprise churn rate.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

PREDICTION ACCURACY

Actual Churns:               47
Predicted (Health <50):      38
Correctly Predicted:         33
Surprise Churns (>60):       14

Accuracy Rate:               70% (target: 70%) ✓
Surprise Churn Rate:         30% (target: <20%) ⚠
False Positive Rate:         28% (target: <30%) ✓

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SCORE-OUTCOME CORRELATION

                    Retention    Expansion    NPS
Health Score        0.62         0.48         0.55
Correlation         Strong       Moderate     Moderate

                    Prior Quarter   Current
Retention Corr.     0.58            0.62  ↑
Expansion Corr.     0.45            0.48  ↑
NPS Corr.           0.52            0.55  ↑

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

LIFT ANALYSIS

Decile    Avg Score    Churn Rate    Lift
1 (High)  12           42%           5.2x  ← Good separation
2         28           31%           3.9x
3         38           22%           2.8x
4         48           15%           1.9x
5         56           11%           1.4x
6         63           9%            1.1x
7         70           7%            0.9x
8         76           5%            0.6x
9         83           3%            0.4x
10 (Low)  91           1%            0.1x

Overall churn rate: 8%
Top decile lift: 5.2x (target: >3x) ✓

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SEGMENT ANALYSIS

Segment         Accuracy    Surprise Rate    Status
Enterprise      62%         38%              ⚠ Needs attention
Mid-Market      74%         22%              ✓ On track
SMB             72%         28%              ✓ On track
Startup         68%         32%              ~ Monitor

Enterprise segment investigation:
- 5 of 14 surprise churns were enterprise
- Common pattern: Champion departure not detected
- Recommendation: Add LinkedIn monitoring signal

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

CALIBRATION CHECK

Score Range    Predicted Risk    Actual Risk    Gap
0-20           85%               78%            -7%
20-40          60%               55%            -5%
40-60          35%               32%            -3%
60-80          15%               12%            -3%
80-100         5%                4%             -1%

Avg Calibration Error: 4% (target: <5%) ✓
Model is slightly overconfident in high-risk scores.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

RECOMMENDATIONS

1. [HIGH] Add champion monitoring to enterprise scoring
2. [MEDIUM] Recalibrate high-risk thresholds
3. [LOW] Review startup segment feature weights
```

### Bad Model Validation Report

```
Health Score Report

Model accuracy: 70%
Churns predicted: 33/47

Status: Working fine.

Problems:
✗ No trend analysis
✗ No segment breakdown
✗ No calibration check
✗ No feature analysis
✗ No actionable recommendations
✗ No comparison to prior period
✗ No investigation of failures
```

### Surprise Churn Analysis Framework

```
Surprise Churn Investigation: AccountName

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

ACCOUNT PROFILE
├── ARR: $85,000
├── Tenure: 18 months
├── Health Score at Churn: 72 (Healthy)
├── Health Score 30 days prior: 74
└── Health Score 90 days prior: 71

CHURN REASON: Competitor displacement

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SIGNAL ANALYSIS: WHAT WE MISSED

Signal                  Present?    In Model?    Why Missed?
─────────────────────────────────────────────────────────────
Competitor research     Yes         No           No intent data
Champion job search     Yes         No           No LinkedIn tracking
Reduced engagement      Subtle      Yes          Below threshold
Support complaints      No          -            No signal
Usage decline           Minor       Yes          Below threshold

ROOT CAUSE: Champion was evaluating alternatives
while maintaining appearance of engagement.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

MODEL IMPROVEMENT OPPORTUNITIES

1. Add intent data signals (competitor research)
2. Add LinkedIn monitoring for key contacts
3. Lower threshold for engagement decline
4. Create composite "quiet leaving" indicator
5. Weight recent trend more heavily

EXPECTED IMPACT: Could have caught this 60 days earlier
```

### Calibration Techniques

| Technique | When to Use | How It Works |
|-----------|-------------|--------------|
| **Platt Scaling** | Score not well-calibrated | Fit logistic regression on scores |
| **Isotonic Regression** | Non-monotonic calibration | Non-parametric adjustment |
| **Temperature Scaling** | Neural network outputs | Single parameter adjustment |
| **Threshold Tuning** | Business-driven calibration | Adjust based on capacity |
| **Segment Adjustment** | Different segments behave differently | Segment-specific thresholds |

### Model Drift Detection

```
Drift Monitoring Dashboard

┌─────────────────────────────────────────────────────────────────┐
│  FEATURE DRIFT MONITORING                                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Feature                   Baseline    Current     Drift       │
│  ────────────────────────────────────────────────────────────  │
│  Usage velocity (30d)      -0.02       -0.08       ⚠ DRIFT    │
│  NPS score                 42          38          ~ Minor     │
│  Support tickets/mo        2.3         2.5         ✓ Stable   │
│  Feature adoption          58%         55%         ✓ Stable   │
│  Champion engagement       0.72        0.68        ~ Minor     │
│                                                                 │
│  ⚠ Alert: Usage velocity distribution shifted significantly   │
│     Recommend: Investigate cause, consider retraining          │
│                                                                 │
├─────────────────────────────────────────────────────────────────┤
│  OUTCOME DRIFT                                                  │
│                                                                 │
│  Metric                    Baseline    Current     Status      │
│  ────────────────────────────────────────────────────────────  │
│  Monthly churn rate        1.5%        1.8%        ~ Monitor   │
│  Score-churn correlation   0.62        0.58        ~ Monitor   │
│  Prediction accuracy       72%         68%         ⚠ Watch    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Validation Schedule

| Activity | Frequency | Owner | Output |
|----------|-----------|-------|--------|
| **Accuracy tracking** | Weekly | Data team | Dashboard update |
| **Surprise churn review** | Per event | CS + Data | Investigation report |
| **Drift monitoring** | Weekly | Data team | Drift alerts |
| **Segment analysis** | Monthly | Data team | Segment report |
| **Full validation** | Quarterly | CS + Data | Validation report |
| **Model retraining** | Quarterly | Data team | New model version |
| **Threshold calibration** | Quarterly | CS leadership | Updated thresholds |

### Threshold Calibration Process

```
Step 1: Analyze current distribution
├── Plot health scores vs. outcomes
├── Identify natural breakpoints
└── Calculate churn rate by score band

Step 2: Assess operational capacity
├── How many at-risk accounts can CSMs handle?
├── What's the cost of false positives?
└── What's the cost of missed churns?

Step 3: Optimize thresholds
├── Set thresholds to balance precision/recall
├── Consider segment-specific adjustments
└── Align with intervention capacity

Step 4: Validate proposed changes
├── Backtest on historical data
├── Calculate expected false positive/negative rates
└── Estimate resource requirements

Step 5: Implement and monitor
├── Update threshold configuration
├── Communicate to CS team
├── Track performance post-change
└── Adjust if needed
```

### Feature Importance Review

| Feature | Current Weight | Q3 Weight | Correlation | Recommendation |
|---------|----------------|-----------|-------------|----------------|
| Usage velocity | 28% | 25% | 0.58 | Maintain |
| NPS trend | 19% | 22% | 0.51 | Maintain |
| Support sentiment | 15% | 14% | 0.42 | Maintain |
| Champion engagement | 13% | 12% | 0.45 | Increase to 15% |
| Feature adoption | 11% | 13% | 0.38 | Reduce to 10% |
| Billing health | 8% | 8% | 0.32 | Maintain |
| Contract signals | 6% | 6% | 0.28 | Maintain |

### Model Governance Checklist

```
□ Validation Process
  □ Weekly accuracy tracking automated
  □ Surprise churn review process defined
  □ Drift alerts configured
  □ Quarterly full validation scheduled

□ Documentation
  □ Model architecture documented
  □ Feature definitions captured
  □ Threshold rationale recorded
  □ Version history maintained

□ Change Management
  □ Change approval process defined
  □ A/B testing capability available
  □ Rollback plan documented
  □ Communication plan for changes

□ Stakeholder Alignment
  □ CS leadership reviews validation reports
  □ Data team owns model maintenance
  □ Feedback loop from CSMs formalized
  □ Executive sponsor engaged

□ Continuous Improvement
  □ New feature experimentation process
  □ Segment-specific tuning allowed
  □ Industry benchmark tracking
  □ Model improvement backlog maintained
```

### Anti-Patterns

- **Set and forget** — Never validating after initial launch
- **Aggregate-only analysis** — Missing segment-specific issues
- **No surprise churn investigation** — Not learning from failures
- **Threshold stagnation** — Never adjusting as business changes
- **Ignoring drift** — Features change meaning over time
- **No documentation** — Model logic in one person's head
- **Validation without action** — Reports with no follow-through
- **Perfect-seeking** — Waiting for 100% accuracy vs. iterating
