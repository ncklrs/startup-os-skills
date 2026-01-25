---
title: Impact Measurement
impact: HIGH
tags: impact, measurement, roi, outcomes
---

## Impact Measurement

**Impact: HIGH**

Shipping features is easy. Proving they worked is hard. Rigorous impact measurement separates "we launched" from "we succeeded."

### The Impact Measurement Framework

```
┌──────────────────────────────────────────────────────────────┐
│                    IMPACT MEASUREMENT                        │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  1. DEFINE SUCCESS                                           │
│     What outcome are we trying to achieve?                   │
│                        ↓                                     │
│  2. ESTABLISH BASELINE                                       │
│     What's the current state?                                │
│                        ↓                                     │
│  3. SET TARGETS                                              │
│     What improvement do we expect?                           │
│                        ↓                                     │
│  4. DESIGN MEASUREMENT                                       │
│     How will we know if we succeeded?                        │
│                        ↓                                     │
│  5. ANALYZE RESULTS                                          │
│     Did we achieve the target?                               │
│                        ↓                                     │
│  6. ATTRIBUTE CAUSATION                                      │
│     Was it because of our change?                            │
│                                                              │
└──────────────────────────────────────────────────────────────┘
```

### Types of Impact Measurement

| Type | Approach | Confidence | When to Use |
|------|----------|------------|-------------|
| **A/B Test** | Randomized control | High | Optimization |
| **Pre/Post** | Before vs after | Medium | When A/B not possible |
| **Cohort Comparison** | New vs old users | Medium | Feature additions |
| **Difference-in-Difference** | Treatment vs control over time | Medium-High | Quasi-experimental |
| **Instrumentation** | Event tracking | N/A | Adoption measurement |

### Setting Success Criteria Before Launch

**Pre-Launch Success Definition:**

```
Feature: Smart Recommendations

Success Criteria Document:
┌──────────────────────────────────────────────────────────────┐
│ Metric                │ Baseline │ Target    │ Measurement  │
├──────────────────────────────────────────────────────────────┤
│ Click-through rate    │   2.1%   │   3.5%    │ A/B test     │
│ Items viewed/session  │   3.2    │   4.5     │ A/B test     │
│ Conversion rate       │   4.8%   │   5.5%    │ A/B test     │
│ Adoption rate         │   N/A    │   40%     │ Tracking     │
│ User satisfaction     │   3.8    │   4.2     │ Survey       │
├──────────────────────────────────────────────────────────────┤
│ Timeline: 30 days post-launch                                │
│ Decision: Keep if 2+ primary metrics hit target              │
│ Owner: PM + Analytics                                        │
└──────────────────────────────────────────────────────────────┘
```

### Impact Measurement Methods

**1. A/B Test Impact**

```
Approach: Randomized experiment
Best for: Feature optimization, UX changes

Example:
┌──────────────────────────────────────────────────────────────┐
│ New Checkout Flow A/B Test Results                           │
├──────────────────────────────────────────────────────────────┤
│ Metric           │ Control │ Treatment │ Lift    │ p-value  │
├──────────────────────────────────────────────────────────────┤
│ Checkout CVR     │  12.4%  │   14.8%   │ +19.4%  │  0.001   │
│ Avg order value  │  $87    │   $89     │  +2.3%  │  0.142   │
│ Cart abandonment │  68%    │   62%     │  -8.8%  │  0.003   │
├──────────────────────────────────────────────────────────────┤
│ Impact: +$142K estimated annual revenue                      │
│ Confidence: HIGH (A/B tested with significance)              │
└──────────────────────────────────────────────────────────────┘
```

**2. Pre/Post Analysis**

```
Approach: Compare before and after launch
Best for: When A/B test not feasible

Example:
┌──────────────────────────────────────────────────────────────┐
│ New Onboarding Pre/Post Analysis                             │
├──────────────────────────────────────────────────────────────┤
│ Period           │ Signup → Active │ D7 Retention           │
├──────────────────────────────────────────────────────────────┤
│ Pre (4 weeks)    │     45%         │     32%                │
│ Post (4 weeks)   │     58%         │     41%                │
│ Change           │    +13pp        │    +9pp                │
├──────────────────────────────────────────────────────────────┤
│ Confounds to consider:                                       │
│ - Seasonality (controlled: same weeks YoY similar)           │
│ - Marketing changes (controlled: no campaign changes)        │
│ - Product changes (controlled: isolated change)              │
├──────────────────────────────────────────────────────────────┤
│ Confidence: MEDIUM (confounds controlled but not eliminated) │
└──────────────────────────────────────────────────────────────┘
```

**3. Cohort Comparison**

```
Approach: Compare users who had feature vs those who didn't
Best for: Gradual rollouts, feature additions

Example:
┌──────────────────────────────────────────────────────────────┐
│ New Feature Cohort Analysis                                  │
├──────────────────────────────────────────────────────────────┤
│ Cohort              │ D30 Retention │ ARPU   │ NPS           │
├──────────────────────────────────────────────────────────────┤
│ With feature        │     48%       │ $42    │  52           │
│ Without feature     │     38%       │ $35    │  41           │
│ Difference          │    +10pp      │ +$7    │ +11           │
├──────────────────────────────────────────────────────────────┤
│ Caution: Self-selection bias possible                        │
│ Users who adopt features may be inherently more engaged      │
└──────────────────────────────────────────────────────────────┘
```

### Calculating Business Impact

**Revenue Impact Calculation:**

```
Feature: Improved Recommendations

Metrics:
- 10,000 daily users exposed
- CTR improved from 2% to 3.5% (+75%)
- CVR on clicked items: 8%
- AOV: $50

Calculation:
Before: 10,000 × 2% × 8% × $50 = $800/day
After:  10,000 × 3.5% × 8% × $50 = $1,400/day
Lift:   $600/day = $219,000/year

Impact Statement:
"Smart Recommendations drive an estimated $219K additional
annual revenue through improved discovery."
```

**LTV Impact Calculation:**

```
Feature: Onboarding Improvements

Metrics:
- 30-day retention improved 10pp (32% → 42%)
- Monthly churn decreased from 8% to 6%
- Average monthly revenue: $30

LTV Calculation:
Before: $30 / 8% = $375 LTV
After:  $30 / 6% = $500 LTV
Lift:   +$125 per customer (+33%)

With 1,000 new customers/month:
Annual LTV impact: $125 × 1,000 × 12 = $1.5M
```

### Good vs Bad Impact Measurement

**Good: Rigorous, Pre-defined**

```
Feature Launch: Team Collaboration

Pre-Launch:
- Success criteria defined
- Baseline metrics captured
- A/B test designed
- 30-day measurement plan

Results (30 days):
┌──────────────────────────────────────────────────────────────┐
│ Metric            │ Goal     │ Result   │ Status            │
├──────────────────────────────────────────────────────────────┤
│ Adoption rate     │ 25%      │ 32%      │ ✓ Exceeded        │
│ Team retention    │ +5pp     │ +8pp     │ ✓ Exceeded        │
│ Seats per team    │ +0.5     │ +0.8     │ ✓ Exceeded        │
│ Support tickets   │ No lift  │ +5%      │ ⚠ Watch           │
├──────────────────────────────────────────────────────────────┤
│ Decision: Ship, address support ticket drivers               │
│ Impact: Est. $340K ARR from seat expansion                   │
└──────────────────────────────────────────────────────────────┘
```

**Bad: Post-hoc, Cherry-picked**

```
Feature Launch: Team Collaboration

Post-Launch:
- "Let's see what metrics improved"
- Found: Page views up 15%!
- Declared: Success!

Problems:
- No pre-defined success criteria
- No baseline comparison
- Cherry-picked positive metric
- Page views ≠ business value
- No causal attribution
```

### Attribution Challenges

| Challenge | Description | Mitigation |
|-----------|-------------|------------|
| **Confounds** | Other things changed | Control for variables |
| **Selection Bias** | Non-random exposure | Randomized experiment |
| **Novelty Effect** | Initial excitement fades | Longer measurement window |
| **Regression to Mean** | Extreme values normalize | Use control groups |
| **Hawthorne Effect** | Behavior changes when watched | Blind experiments |

### Impact Reporting Template

```
┌──────────────────────────────────────────────────────────────┐
│                    IMPACT REPORT                             │
│                 Feature: Smart Search                        │
├──────────────────────────────────────────────────────────────┤
│ SUMMARY                                                      │
│ Smart Search improved search conversion by 23% in A/B test,  │
│ generating estimated $180K annual revenue.                   │
├──────────────────────────────────────────────────────────────┤
│ HYPOTHESIS                                                   │
│ AI-powered search suggestions would increase search→result   │
│ clicks by 20% by surfacing more relevant results.            │
├──────────────────────────────────────────────────────────────┤
│ METHODOLOGY                                                  │
│ - A/B test, 50/50 split                                      │
│ - n = 45,000 (22,500/variant)                                │
│ - Duration: 28 days                                          │
│ - Primary metric: Search→click rate                          │
├──────────────────────────────────────────────────────────────┤
│ RESULTS                                                      │
│ Metric              │ Control │ Treatment │ p-value         │
│ Search→click rate   │  18.2%  │   22.4%   │ <0.001          │
│ Searches/session    │   1.8   │    2.1    │  0.003          │
│ Purchase after search│  4.2%  │   4.8%    │  0.021          │
├──────────────────────────────────────────────────────────────┤
│ BUSINESS IMPACT                                              │
│ - 23% more users find what they're looking for               │
│ - 14% increase in search-driven purchases                    │
│ - Estimated $180K additional annual revenue                  │
├──────────────────────────────────────────────────────────────┤
│ RECOMMENDATION                                               │
│ Ship to 100%. Consider extending to mobile app.              │
├──────────────────────────────────────────────────────────────┤
│ LEARNINGS                                                    │
│ - AI suggestions most effective for complex queries          │
│ - Less impact for branded/simple searches                    │
│ - Mobile users engaged more with suggestions                 │
└──────────────────────────────────────────────────────────────┘
```

### Impact Measurement Cadence

| Timeframe | Focus | Activities |
|-----------|-------|------------|
| **Pre-Launch** | Definition | Success criteria, baseline, measurement plan |
| **Launch +7d** | Adoption | Is feature being used? Any bugs? |
| **Launch +30d** | Primary | Did we hit success criteria? |
| **Launch +90d** | Sustained | Are gains holding? Any degradation? |
| **Quarterly** | Portfolio | Which features drove most impact? |

### Anti-Patterns

- **Post-hoc success definition** — Defining success after seeing results
- **Vanity metrics** — Measuring what looks good, not what matters
- **No baseline** — Can't measure lift without starting point
- **Ignoring context** — External factors explain "lift"
- **Single metric obsession** — Winning primary while losing guardrails
- **Short-term thinking** — Week 1 results ≠ long-term impact
- **No follow-up** — Measuring once, never checking if it holds
- **Correlation claims** — "Feature users retain better" (selection bias)
