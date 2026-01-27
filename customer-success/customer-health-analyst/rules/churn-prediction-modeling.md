---
title: Churn Prediction Modeling
impact: CRITICAL
tags: churn-prediction, machine-learning, risk-scoring, early-warning
---

## Churn Prediction Modeling

**Impact: CRITICAL**

Effective churn prediction gives you 60-90 days of lead time to intervene. A well-calibrated model can reduce churn by 15-30% by enabling proactive outreach to at-risk accounts before they decide to leave.

### The Churn Prediction Pipeline

```
┌──────────────────────────────────────────────────────────────────┐
│                    CHURN PREDICTION PIPELINE                     │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  DATA           FEATURES         MODEL           SCORING        │
│  COLLECTION  →  ENGINEERING  →   TRAINING   →   & ALERTS       │
│                                                                  │
│  • Product       • Usage decay    • Logistic     • Daily risk   │
│  • CRM           • Engagement     • Random       • Threshold    │
│  • Support       • Sentiment      • XGBoost      • Routing      │
│  • Financial     • Growth         • Neural       • Actions      │
│                                                                  │
├──────────────────────────────────────────────────────────────────┤
│                    FEEDBACK LOOP                                 │
│                                                                  │
│           Actual Outcomes → Model Refinement → Improved Accuracy │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Feature Categories for Churn Models

| Category | Features | Predictive Value |
|----------|----------|------------------|
| **Usage Metrics** | DAU/MAU, feature adoption, session depth | High |
| **Usage Trends** | 30/60/90-day slopes, velocity changes | Very High |
| **Engagement** | NPS, CSM touchpoints, email responsiveness | High |
| **Support** | Ticket volume, sentiment, escalations | High |
| **Financial** | Payment issues, contract length, pricing tier | Medium |
| **Organizational** | Champion status, stakeholder changes | High |
| **Firmographics** | Company size, industry, growth stage | Medium |
| **Temporal** | Tenure, contract timing, seasonality | Medium |

### Good Feature Engineering

```
Feature: Usage Velocity (30-Day)

Definition:
velocity_30d = (usage_current - usage_30d_ago) / usage_30d_ago

Why It's Predictive:
- Captures direction AND magnitude of change
- Declining velocity precedes churn by 60-90 days
- More predictive than static usage levels

Implementation:
SELECT
  customer_id,
  (current_usage - lag_30d_usage) / NULLIF(lag_30d_usage, 0) as velocity_30d
FROM customer_usage
WHERE lag_30d_usage > 0

Feature Distribution:
- Retained customers: mean velocity = +0.05
- Churned customers: mean velocity = -0.28
- Separation is clear and actionable
```

### Bad Feature Engineering

```
Feature: Total Logins (All-Time)

Problems:
✗ Doesn't account for tenure
✗ No directional information
✗ Old customers always score higher
✗ Not predictive of future behavior

Better Alternative:
- Login frequency (logins per week)
- Login trend (this month vs. last month)
- Days since last login

Feature Reality:
- Retained customers: mean = 1,247 logins
- Churned customers: mean = 892 logins
- Overlap is massive, low predictive value
```

### Model Selection Guide

| Model Type | Pros | Cons | Best For |
|------------|------|------|----------|
| **Logistic Regression** | Interpretable, fast | Less accurate | Baseline, regulated industries |
| **Random Forest** | Handles non-linear, robust | Less interpretable | Medium datasets |
| **XGBoost** | High accuracy, handles imbalance | Complex tuning | Large datasets, accuracy focus |
| **Neural Network** | Captures complex patterns | Black box, needs lots of data | Very large datasets |
| **Survival Analysis** | Time-to-event prediction | Specialized | When timing matters |

### Model Training Process

```
Step 1: Data Preparation
├── Define churn (90-day non-renewal? Contract cancellation?)
├── Set observation window (features from T-90 to T-0)
├── Set outcome window (churn in next 90 days)
└── Handle class imbalance (SMOTE, class weights)

Step 2: Feature Selection
├── Calculate feature importance (univariate)
├── Remove correlated features (>0.8 correlation)
├── Engineer interaction features
└── Normalize/standardize as needed

Step 3: Model Training
├── Split: 70% train, 15% validation, 15% test
├── Train multiple model types
├── Tune hyperparameters on validation set
└── Select best model by validation AUC

Step 4: Model Evaluation
├── Test set performance (AUC, precision, recall)
├── Calibration check (predicted vs. actual probabilities)
├── Feature importance review
└── Business metric simulation

Step 5: Deployment
├── Productionize scoring pipeline
├── Set up monitoring and alerts
├── Document model and features
└── Plan retraining schedule
```

### Model Performance Metrics

| Metric | Formula | Target | Interpretation |
|--------|---------|--------|----------------|
| **AUC-ROC** | Area under ROC curve | >0.75 | Discrimination ability |
| **Precision** | TP / (TP + FP) | >0.60 | Of predicted churns, % correct |
| **Recall** | TP / (TP + FN) | >0.70 | Of actual churns, % caught |
| **F1 Score** | 2 × (P × R) / (P + R) | >0.65 | Balanced accuracy |
| **Lift** | Model precision / Base rate | >3x | Improvement over random |

### Threshold Selection

```
Tradeoff: Precision vs. Recall

High Threshold (e.g., >0.7 probability):
✓ High precision (fewer false positives)
✗ Low recall (miss some actual churns)
→ Use when intervention is expensive

Low Threshold (e.g., >0.3 probability):
✓ High recall (catch more actual churns)
✗ Low precision (more false positives)
→ Use when missing churn is expensive

Optimal Threshold:
- Calculate cost of false positive (unnecessary intervention)
- Calculate cost of false negative (missed churn)
- Find threshold that minimizes total expected cost
```

### Risk Tiering System

| Tier | Probability | % of Customers | Action |
|------|-------------|----------------|--------|
| **Critical** | >70% | 5-10% | Immediate executive intervention |
| **High** | 50-70% | 10-15% | CSM manager involvement |
| **Medium** | 30-50% | 15-20% | CSM proactive outreach |
| **Low** | 10-30% | 30-40% | Standard monitoring |
| **Minimal** | <10% | 20-30% | Expansion focus |

### Early Warning System Design

```
┌──────────────────────────────────────────────────────────────────┐
│                    EARLY WARNING SYSTEM                          │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  Daily Scoring Pipeline:                                         │
│  ├── Pull latest customer data                                   │
│  ├── Calculate features                                          │
│  ├── Score all customers                                         │
│  └── Update risk tiers                                           │
│                                                                  │
│  Alert Triggers:                                                 │
│  ├── Risk tier change (e.g., Low → Medium)                      │
│  ├── Probability increase >20 points                             │
│  ├── Critical signals detected                                   │
│  └── Combination triggers                                        │
│                                                                  │
│  Alert Routing:                                                  │
│  ├── Critical → CSM + Manager + VP (Slack + Email)              │
│  ├── High → CSM + Manager (Email)                               │
│  ├── Medium → CSM (Dashboard + Email)                           │
│  └── Low → Dashboard only                                        │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Intervention Optimization

| Lead Time | Intervention Success Rate | Recommended Actions |
|-----------|---------------------------|---------------------|
| 90+ days | 55-65% | Strategic value review |
| 60-90 days | 45-55% | Executive engagement |
| 30-60 days | 30-40% | Intensive support |
| <30 days | 15-25% | Save offer |
| At cancellation | 5-15% | Exit interview + win-back plan |

### Model Monitoring Dashboard

```
Churn Prediction Model Health

┌─────────────────────────────────────────────────────────────┐
│  MODEL PERFORMANCE (Rolling 90 Days)                        │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  AUC-ROC:          0.78 (target: >0.75)        ✓           │
│  Precision:        0.62 (target: >0.60)        ✓           │
│  Recall:           0.71 (target: >0.70)        ✓           │
│  Lift at 10%:      4.2x (target: >3x)          ✓           │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  PREDICTION ACCURACY                                        │
│                                                             │
│  Actual Churns:         47                                  │
│  Predicted (>50%):      38                                  │
│  Correctly Predicted:   33                                  │
│  Surprise Churns:       14                                  │
│  False Alarms:          5                                   │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  FEATURE IMPORTANCE (Top 5)                                 │
│                                                             │
│  1. Usage velocity (30d)      ████████████  28%            │
│  2. NPS trend                 ████████      19%            │
│  3. Support sentiment         ███████       15%            │
│  4. Champion engagement       ██████        13%            │
│  5. Feature adoption trend    █████         11%            │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│  ALERTS                                                     │
│                                                             │
│  ⚠ Recall dropped 5% vs. prior period                      │
│  ⚠ Feature drift detected in usage metrics                 │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Model Maintenance Schedule

| Activity | Frequency | Owner | Deliverable |
|----------|-----------|-------|-------------|
| Accuracy review | Weekly | Data team | Performance report |
| Feature drift check | Weekly | Data team | Drift alerts |
| Threshold review | Monthly | CS + Data | Updated thresholds |
| Full retraining | Quarterly | Data team | New model version |
| Feature review | Quarterly | CS + Data | Feature updates |
| Major overhaul | Annually | Data team | Architecture review |

### Churn Model Checklist

```
□ Data Quality
  □ Churn definition is clear and consistent
  □ Historical data covers 12+ months
  □ Feature data is complete and accurate
  □ Class imbalance addressed appropriately

□ Feature Engineering
  □ Features are predictive (tested)
  □ No data leakage (future info in features)
  □ Features are interpretable
  □ Trends included, not just levels

□ Model Development
  □ Train/validation/test split done properly
  □ Cross-validation used for tuning
  □ Multiple model types compared
  □ Hyperparameters optimized

□ Model Evaluation
  □ Performance meets targets
  □ Model is calibrated (probabilities accurate)
  □ No obvious bias by segment
  □ Business simulation validates value

□ Deployment
  □ Scoring pipeline automated
  □ Monitoring in place
  □ Alerts configured
  □ Documentation complete

□ Operations
  □ Retraining schedule defined
  □ Drift monitoring active
  □ Feedback loop from CS team
  □ Regular accuracy reviews
```

### Anti-Patterns

- **Predicting the past** — Data leakage giving false accuracy
- **One model fits all** — Ignoring segment differences
- **Set and forget** — Models decay without retraining
- **Ignoring false positives** — Intervention fatigue from bad predictions
- **Probability as certainty** — Treating 60% risk as definite churn
- **No action mapping** — Predictions without intervention playbooks
- **Over-engineering** — Complex models when simple works
- **Ignoring surprise churns** — Not investigating model failures
