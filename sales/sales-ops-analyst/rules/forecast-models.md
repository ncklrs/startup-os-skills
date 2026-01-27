---
title: Sales Forecasting Models
impact: CRITICAL
tags: forecasting, prediction, models, accuracy, AI
---

## Sales Forecasting Models

**Impact: CRITICAL**

Accurate forecasting is the foundation of business planning. It affects hiring, cash flow, investor confidence, and strategic decisions. Get it wrong, and the ripple effects are massive.

### Forecasting Methodologies

| Method | Description | Best For | Accuracy |
|--------|-------------|----------|----------|
| **Rep Commit** | Reps predict their own deals | Early stage, small teams | Low-Medium |
| **Manager Judgment** | Managers adjust rep commits | Established process | Medium |
| **Weighted Pipeline** | Stage probability × amount | Mature pipeline | Medium |
| **Historical Analysis** | Based on past conversion rates | Stable business | Medium-High |
| **AI/ML Models** | Pattern-based prediction | Large datasets | High |
| **Hybrid** | Combine multiple methods | Most companies | Highest |

### Forecast Category Framework

```
┌─────────────────────────────────────────────────────────────┐
│                    FORECAST CATEGORIES                       │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│   COMMIT          BEST CASE       PIPELINE        OMITTED   │
│   ██████          ████████        ██████████      ████      │
│                                                              │
│   "Will close"    "Should close"  "Could close"  "Won't     │
│   >90% likely     70-89% likely   30-69% likely   close"    │
│                                                              │
│   Deals with:     Deals with:     Deals with:     Deals:    │
│   - Verbal yes    - Champion      - Active        - Stalled │
│   - Contract out  - Budget ok     - Interest      - No fit  │
│   - Close <30d    - Timeline ok   - Early stage   - Lost    │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### Weighted Pipeline Calculation

**Stage-Based Probability:**

| Stage | Default Probability | Adjusted (Your Data) |
|-------|---------------------|---------------------|
| Qualification | 10% | 8% |
| Discovery | 20% | 18% |
| Demo/Evaluation | 40% | 35% |
| Proposal | 60% | 55% |
| Negotiation | 80% | 78% |
| Closed Won | 100% | 100% |

**Weighted Forecast Calculation:**

```
Deal 1: $100K at Proposal (55%)     = $55,000
Deal 2: $50K at Demo (35%)          = $17,500
Deal 3: $200K at Negotiation (78%)  = $156,000
Deal 4: $75K at Discovery (18%)     = $13,500
                                      ─────────
Weighted Pipeline Forecast:         = $242,000
```

### AI/ML Forecasting Approach

**Feature Engineering for Deal Prediction:**

```python
# Features that predict deal outcome
deal_features = {
    # Deal characteristics
    'amount': deal.amount,
    'days_in_stage': (today - deal.stage_date).days,
    'days_to_close': (deal.close_date - today).days,
    'discount_percent': deal.discount / deal.list_price,

    # Engagement signals
    'email_count_30d': activities.filter(type='email', days=30).count(),
    'meeting_count_30d': activities.filter(type='meeting', days=30).count(),
    'days_since_last_activity': (today - last_activity.date).days,
    'stakeholder_count': deal.contacts.count(),
    'has_champion': deal.contacts.filter(role='Champion').exists(),
    'has_decision_maker': deal.contacts.filter(role='Decision Maker').exists(),

    # Historical patterns
    'rep_win_rate': rep.historical_win_rate,
    'segment_win_rate': segment.historical_win_rate,
    'similar_deal_outcome': similar_deals.avg_win_rate,

    # External signals
    'company_growth_signal': company.hiring_trend,
    'intent_score': intent_data.score,
    'competitor_mention': gong_calls.competitor_mentions > 0
}
```

**Model Output:**

```
Deal: Acme Corp - Enterprise License
─────────────────────────────────────
AI Win Probability: 73%
Rep Commit: Best Case

Key Factors (SHAP analysis):
✅ +15% Champion identified and engaged
✅ +12% 5 meetings in last 30 days
✅ +8%  Similar deals closed at 68% rate
⚠️ -5%  Close date pushed twice
⚠️ -7%  Days in Proposal stage above average

Recommendation: Move to Commit if close date confirmed
```

### Forecast Accuracy Measurement

**Accuracy Metrics:**

| Metric | Formula | Target |
|--------|---------|--------|
| **Forecast Accuracy** | 1 - |Forecast - Actual| / Actual | >85% |
| **Weighted Error** | Σ|Forecast - Actual| × Deal Size / Σ Deal Size | <15% |
| **Bias** | (Forecast - Actual) / Actual (directional) | ±5% |
| **Commit Accuracy** | Commit Closed Won / Commit Total | >80% |

**Forecast Tracking Dashboard:**

```
┌────────────────────────────────────────────────────────────┐
│             FORECAST ACCURACY TRACKING - Q1 2025           │
├────────────────────────────────────────────────────────────┤
│                                                             │
│ Week 1 Forecast: $2.1M   │   Actual: $1.85M               │
│ Accuracy: 88%            │   Bias: +14% (over-forecast)   │
│                                                             │
│ ┌────────────────────────────────────────────────────────┐ │
│ │        Week 1    Week 2    Week 3    EoQ Final        │ │
│ │ Commit  $1.2M    $1.4M     $1.6M     $1.85M    ✓     │ │
│ │ Best    $1.8M    $1.9M     $2.0M     $1.85M    -     │ │
│ │ Pipe    $3.5M    $3.2M     $2.8M     $1.85M    -     │ │
│ │ Actual    -        -         -       $1.85M          │ │
│ └────────────────────────────────────────────────────────┘ │
│                                                             │
│ Rep Accuracy Breakdown:                                     │
│ Sarah: 92% ████████████████████                            │
│ Mike:  78% ████████████████                                │
│ Lisa:  85% █████████████████                               │
│ Tom:   65% █████████████           ⚠️ Needs coaching       │
└────────────────────────────────────────────────────────────┘
```

### Forecast Call Process

**Weekly Forecast Call Agenda:**

```
Duration: 30-45 minutes
Attendees: VP Sales, Directors, Sales Ops

1. Pipeline Review (10 min)
   - Total pipeline vs coverage target
   - New pipeline created this week
   - Pipeline at risk (aging, no activity)

2. Commit Review (15 min)
   - Each rep's commit deals
   - Changes from last week (add/remove/amount)
   - Risk assessment per deal

3. Upside Discussion (10 min)
   - Best case opportunities
   - What needs to happen to close

4. Actions & Risks (5 min)
   - Deals needing escalation
   - Resource allocation decisions
   - Follow-up items

Output: Updated forecast in system within 2 hours
```

### Forecast Hygiene Rules

| Rule | Enforcement | Consequence |
|------|-------------|-------------|
| Close date must be realistic | Validation: can't be >90 days if in Negotiation | Blocked save |
| Commit requires next steps | Task must exist with date <7 days | Cannot add to Commit |
| Push count tracked | Auto-increment when close date moves | Visible in reports |
| Amount changes logged | Field history tracking | Audit trail |
| No deal >120 days in stage | Auto-flag for review | Manager alert |

### Common Forecasting Mistakes

**Mistake: Sandbagging**
```
Pattern: Rep consistently commits 80% of what they close
Impact: Under-forecasting leads to missed opportunities
Fix: Track commit-to-close ratio, coach on accuracy
```

**Mistake: Happy Ears**
```
Pattern: Rep commits deals without buying signals
Impact: Over-forecasting damages credibility
Fix: Require documented next steps, decision maker access
```

**Mistake: Close Date Fiction**
```
Pattern: Every deal closes "end of month" or "end of quarter"
Impact: Forecast accuracy drops, hockey stick quarters
Fix: Validate close dates match buyer timeline
```

### Forecasting Tools

| Tool | Strength | Integration |
|------|----------|-------------|
| **Salesforce CRM Analytics** | Native, good for SFDC shops | Native |
| **Clari** | AI forecasting, deal inspection | SFDC, HubSpot |
| **Gong Forecast** | Conversation-based signals | SFDC + Gong |
| **InsightSquared** | Analytics + forecasting | SFDC, HubSpot |
| **Aviso** | AI-driven, enterprise | SFDC |
| **BoostUp** | Revenue operations | SFDC, HubSpot |

### Anti-Patterns

- **Gut-based forecasting** — No data, just hope
- **Single methodology** — Rep commit only, no validation
- **Quarterly spikes** — All deals close last week of quarter
- **No accountability** — Forecast misses without consequences
- **Delayed updates** — Weekly forecast calls with stale data
- **Ignoring trends** — Not adjusting for seasonality or market changes
- **One-size-fits-all** — Same forecast method for $10K and $1M deals
- **No post-mortem** — Not analyzing why forecasts were wrong
