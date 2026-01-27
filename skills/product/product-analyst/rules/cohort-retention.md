---
title: Cohort Analysis and Retention
impact: CRITICAL
tags: cohort, retention, churn, lifecycle
---

## Cohort Analysis and Retention

**Impact: CRITICAL**

Cohort analysis separates the signal from the noise. It answers: "Are things getting better?" by comparing groups of users who share a common starting point.

### What is a Cohort?

A cohort is a group of users who share a characteristic, typically their signup date (acquisition cohort) or first action date (behavioral cohort).

```
Week 1 Cohort:  All users who signed up during Week 1
Week 2 Cohort:  All users who signed up during Week 2
...

Compare: How does Week 5 cohort perform vs Week 1 cohort?
```

### The Classic Retention Table

```
         Week 0   Week 1   Week 2   Week 3   Week 4   Week 5
Cohort   ──────   ──────   ──────   ──────   ──────   ──────
Jan 1    1,000    450      380      320      290      280
Jan 8    1,200    540      465      400      360        -
Jan 15   1,100    520      440      385        -        -
Jan 22   1,300    610      530        -        -        -
Jan 29   1,400    650        -        -        -        -

As Percentages:
         Week 0   Week 1   Week 2   Week 3   Week 4   Week 5
         ──────   ──────   ──────   ──────   ──────   ──────
Jan 1    100%     45%      38%      32%      29%      28%
Jan 8    100%     45%      39%      33%      30%       -
Jan 15   100%     47%      40%      35%       -        -
Jan 22   100%     47%      41%       -        -        -
Jan 29   100%     46%       -        -        -        -
```

**Reading the table:**
- **Rows:** Different cohorts (by signup week)
- **Columns:** Time periods since signup
- **Diagonal:** Same calendar week across cohorts
- **Trend right:** How retention evolves over time for a cohort
- **Trend down:** How retention improves/degrades for newer cohorts

### Types of Retention Metrics

| Type | Definition | Use Case |
|------|------------|----------|
| **N-Day Retention** | % returning on exactly day N | Mobile apps, daily products |
| **N-Day Rolling** | % still active after day N | Subscription products |
| **Unbounded** | % returning on or after day N | Casual use products |
| **Bracket/Range** | % active within a time window | Weekly/monthly products |

**Examples:**

```
N-Day (D7):
  Active on exactly day 7 / Total users = 22%

N-Day Rolling (D7):
  Active at least once days 7-14 / Total users = 35%

Unbounded (D7):
  Active on day 7 OR any day after / Total users = 45%

Bracket (Week 2):
  Active during days 8-14 / Total users = 32%
```

### Retention Curves

```
100% ┤
     │ ●
 80% ┤  ╲
     │   ●
 60% ┤    ╲
     │     ●───●───●───●───●───●  ← Good: Flattening
 40% ┤
     │         ●
 20% ┤          ╲
     │           ●───●
  0% ┤                ╲───●───●  ← Bad: Still declining
     └────────────────────────────
       W0  W1  W2  W3  W4  W5  W6  W7  W8
```

**What the curve tells you:**
- **Steep early drop:** Activation problem
- **Gradual continued decline:** Value realization problem
- **Flattens at high %:** Strong product-market fit
- **Never flattens:** Fundamental value problem

### Cohort Analysis Techniques

**1. Acquisition Cohort Analysis**
Group by signup date to measure:
- Is retention improving over time?
- Did a product change help/hurt retention?
- Are newer users more/less engaged?

```
Question: Are we getting better at retaining users?
Compare: Jan cohort W4 retention vs March cohort W4 retention
Result: 29% → 35% improvement
Insight: Onboarding improvements are working
```

**2. Behavioral Cohort Analysis**
Group by first action or behavior to measure:
- Which first actions predict retention?
- What separates engaged vs churned users?
- What's the "aha moment"?

```
Cohort by first action:
┌──────────────────────────────────────────────┐
│ First Action        │ W4 Retention │ LTV    │
├──────────────────────────────────────────────┤
│ Created project     │    42%       │ $280   │
│ Invited team member │    58%       │ $420   │
│ Imported data       │    65%       │ $510   │
│ Just browsed        │    12%       │ $45    │
└──────────────────────────────────────────────┘

Insight: Users who import data retain 5x better
Action: Prioritize data import in onboarding
```

**3. Segment Cohort Analysis**
Compare retention across user segments:

```
W4 Retention by Segment:
┌──────────────────────────────────────────────┐
│ Segment              │ W4 Retention          │
├──────────────────────────────────────────────┤
│ Enterprise (500+)    │    72%                │
│ Mid-market (50-500)  │    48%                │
│ SMB (10-50)          │    35%                │
│ Micro (<10)          │    18%                │
└──────────────────────────────────────────────┘

Insight: Enterprise retains 4x better than micro
Action: Shift ICP focus or improve SMB experience
```

### Calculating Key Retention Metrics

**Churn Rate**
```
Monthly Churn = Customers lost in month / Customers at start of month
Example: 50 churned / 1,000 starting = 5% monthly churn
Annual Churn ≈ 1 - (1 - Monthly Churn)^12 = 46% annual churn
```

**Retention Rate**
```
Retention Rate = 1 - Churn Rate
Example: 1 - 5% = 95% monthly retention
```

**Customer Lifetime (Average)**
```
Average Lifetime = 1 / Churn Rate
Example: 1 / 5% = 20 months average lifetime
```

**Net Revenue Retention (NRR)**
```
NRR = (Starting MRR + Expansion - Contraction - Churn) / Starting MRR
Example: ($100k + $15k - $5k - $8k) / $100k = 102% NRR
```

### Good vs Bad Retention Curves

**Good: Consumer Subscription (Spotify-like)**
```
Day    Retention    Interpretation
───────────────────────────────────
D1     70%          Good first session
D7     45%          Habit forming
D30    30%          Solid monthly engagement
D90    22%          Core user base forming
D180   18%          Plateau = product-market fit
```

**Bad: Leaky Bucket**
```
Day    Retention    Interpretation
───────────────────────────────────
D1     50%          Many bouncing immediately
D7     25%          Half gone in a week
D30    8%           Hemorrhaging users
D90    2%           Almost no one stays
D180   0.5%         Fundamental value problem
```

**Good: B2B SaaS**
```
Month  Retention    Interpretation
───────────────────────────────────
M1     92%          Normal startup churn
M3     88%          Onboarding complete
M6     85%          Sticky integrations
M12    80%          Annual renewal strong
M24    75%          Long-term value delivered
```

### Finding Your "Aha Moment"

The aha moment is the action or experience that predicts retention.

**Analysis approach:**
```
1. Define retained (e.g., active at W4)
2. List candidate behaviors in W1
3. Calculate correlation with retention
4. Find the threshold that maximizes separation

Candidate Analysis:
┌─────────────────────────────────────────────────────────┐
│ W1 Behavior           │ W4 Retention │ Correlation     │
├─────────────────────────────────────────────────────────┤
│ Created 1 project     │    35%       │ 0.42            │
│ Created 3+ projects   │    62%       │ 0.71            │
│ Invited 1 teammate    │    48%       │ 0.55            │
│ Invited 3+ teammates  │    78%       │ 0.85 ← Aha!     │
│ Used mobile app       │    52%       │ 0.58            │
└─────────────────────────────────────────────────────────┘

Aha moment: Invite 3+ teammates in week 1
```

### Resurrection Analysis

```
Resurrection Rate = Resurrected users / Churned users

Monthly resurrection:
┌────────────────────────────────────────────────┐
│ Churned Month │ Resurrected │ Rate │ Via      │
├────────────────────────────────────────────────┤
│ January       │    45       │ 12%  │ Email    │
│ February      │    38       │ 10%  │ Feature  │
│ March         │    52       │ 14%  │ Email    │
└────────────────────────────────────────────────┘

Insight: Win-back emails resurrect ~12% of churned
Action: Invest in better resurrection campaigns
```

### Retention Improvement Tactics

| Problem | Indicators | Tactics |
|---------|------------|---------|
| **D1 drop-off** | <60% D1 retention | Improve onboarding, reduce friction |
| **W1 decline** | Steep W1 curve | Strengthen habit loops, add value faster |
| **No plateau** | Curve never flattens | Find and amplify aha moment |
| **Segment variance** | Wide cohort spread | Focus on high-retaining segments |
| **Seasonal churn** | Predictable drops | Proactive engagement before drop |

### Anti-Patterns

- **Only tracking DAU/MAU** — Masks cohort-level problems
- **Ignoring early churn** — Most churn happens in first week
- **Average-only analysis** — Segment differences matter
- **Short windows** — Need 3-6 months for meaningful curves
- **No resurrection tracking** — Churned users can come back
- **Vanity retention** — Counting logins without value delivery
- **Static analysis** — Retention should improve over time
