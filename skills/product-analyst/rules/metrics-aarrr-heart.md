---
title: AARRR and HEART Frameworks
impact: CRITICAL
tags: metrics, framework, aarrr, heart, pirate-metrics
---

## AARRR and HEART Frameworks

**Impact: CRITICAL**

Two proven frameworks for structuring your product metrics. AARRR focuses on lifecycle stages; HEART focuses on user experience dimensions.

### AARRR (Pirate Metrics)

Developed by Dave McClure for startup metrics. Tracks the user lifecycle funnel.

| Stage | Core Question | Example Metrics | Typical Owner |
|-------|---------------|-----------------|---------------|
| **Acquisition** | Where do users come from? | Signups by channel, CAC, landing page conversion | Growth/Marketing |
| **Activation** | Do they experience value? | Onboarding completion, time-to-first-value, aha moment | Product/Growth |
| **Retention** | Do they come back? | D1/D7/D30, MAU/DAU ratio, resurrection rate | Product |
| **Revenue** | Do they pay? | Conversion rate, ARPU, LTV, expansion rate | Product/Finance |
| **Referral** | Do they tell others? | Viral coefficient, NPS, referral conversion | Growth/Product |

### AARRR Deep Dive: Metrics by Stage

**Acquisition Metrics**
```
┌─────────────────────────────────────────────────────────────┐
│  Traffic Sources          │  Signups by source              │
│  Channel CAC              │  Cost per signup by channel     │
│  Landing Page CVR         │  Visitor → Signup rate          │
│  Signup Completion        │  Started → Completed signup     │
│  Channel Mix              │  % of signups by channel        │
└─────────────────────────────────────────────────────────────┘
```

**Activation Metrics**
```
┌─────────────────────────────────────────────────────────────┐
│  Setup Completion Rate    │  % completing onboarding        │
│  Time to First Value      │  Signup → Core action (minutes) │
│  Aha Moment Rate          │  % reaching activation event    │
│  Day 1 Return Rate        │  % returning within 24 hours    │
│  Feature Discovery        │  % using 2+ features in week 1  │
└─────────────────────────────────────────────────────────────┘
```

**Retention Metrics**
```
┌─────────────────────────────────────────────────────────────┐
│  D1/D7/D30 Retention      │  % returning on day N           │
│  Weekly Retention Curve   │  % active each week post-signup │
│  Stickiness (DAU/MAU)     │  Daily engagement ratio         │
│  Churn Rate               │  % lost per period              │
│  Resurrection Rate        │  % of churned who return        │
└─────────────────────────────────────────────────────────────┘
```

**Revenue Metrics**
```
┌─────────────────────────────────────────────────────────────┐
│  Free → Paid Conversion   │  % converting to paid           │
│  Trial → Paid Conversion  │  % of trials converting         │
│  ARPU/ARPA                │  Average revenue per user/acct  │
│  LTV                      │  Lifetime value                 │
│  Expansion Revenue %      │  % revenue from existing        │
└─────────────────────────────────────────────────────────────┘
```

**Referral Metrics**
```
┌─────────────────────────────────────────────────────────────┐
│  NPS                      │  Net Promoter Score             │
│  Viral Coefficient (K)    │  Invites × Invite CVR           │
│  Referral Rate            │  % users who refer              │
│  Referral Conversion      │  Referred visitor → signup rate │
│  Organic Word-of-Mouth    │  Direct/organic signup %        │
└─────────────────────────────────────────────────────────────┘
```

### HEART Framework (Google)

Developed by Kerry Rodden at Google. Focuses on user experience quality.

| Dimension | What It Measures | Signal Types | Example Metrics |
|-----------|------------------|--------------|-----------------|
| **Happiness** | User satisfaction | Attitudinal | NPS, CSAT, ease-of-use |
| **Engagement** | Involvement depth | Behavioral | Sessions/week, actions/session |
| **Adoption** | Uptake of features | Behavioral | New feature users, breadth |
| **Retention** | Continued usage | Behavioral | Retention rate, churn |
| **Task Success** | Efficiency | Behavioral | Completion rate, time-on-task |

### HEART Goals-Signals-Metrics (GSM)

For each HEART dimension, define:

| Step | Definition | Example (File Sharing App) |
|------|------------|---------------------------|
| **Goal** | What experience outcome? | Users successfully share files |
| **Signal** | What indicates goal met? | Completed file shares |
| **Metric** | How do we measure signal? | Files shared per active user |

**Full HEART GSM Example:**

| Dimension | Goal | Signal | Metric |
|-----------|------|--------|--------|
| **Happiness** | Users satisfied with sharing | Survey responses | CSAT score on share flow |
| **Engagement** | Users share frequently | Share activity | Shares per week per user |
| **Adoption** | New users start sharing | First share complete | % of new users who share in W1 |
| **Retention** | Users keep sharing | Repeated share behavior | Week-over-week share retention |
| **Task Success** | Sharing is easy | Successful shares | Share completion rate, time to share |

### When to Use Which Framework

| Use AARRR When | Use HEART When |
|----------------|----------------|
| Analyzing full lifecycle | Deep-diving on UX quality |
| Cross-functional alignment | Product team focus |
| Growth modeling | Feature-level analysis |
| Business metrics review | User experience audit |
| Startup/scale phase | Mature product optimization |

### Combining AARRR + HEART

The frameworks complement each other:

```
AARRR Stage          HEART Dimensions to Apply
───────────────────────────────────────────────
Acquisition     →    Task Success (signup flow)
Activation      →    Task Success, Adoption, Happiness
Retention       →    Engagement, Retention, Happiness
Revenue         →    Task Success (purchase flow), Happiness
Referral        →    Happiness (NPS), Engagement
```

### Good vs Bad Example: AARRR Implementation

**Good: Clear, Measurable, Actionable**
```
Company: Analytics SaaS Tool

Acquisition:
- Metric: Signups by channel
- Target: 500 signups/month, <$50 CAC

Activation:
- Metric: First dashboard created within 7 days
- Target: 60% of signups

Retention:
- Metric: Weekly active users (ran 1+ query)
- Target: 45% W4 retention

Revenue:
- Metric: Trial → Paid conversion
- Target: 12% within 30 days

Referral:
- Metric: NPS, organic signup %
- Target: NPS > 50, 30%+ organic
```

**Bad: Vague, Unmeasurable, No Targets**
```
Company: Analytics SaaS Tool

Acquisition: "Get more users"
Activation: "Users like the product"
Retention: "Keep users coming back"
Revenue: "Make money"
Referral: "Users recommend us"

Problems:
- No specific metrics defined
- No targets to measure against
- No way to know if improving
- No team accountability
```

### HEART Implementation Mistakes

| Mistake | Problem | Fix |
|---------|---------|-----|
| **Tracking all dimensions everywhere** | Overwhelming, unfocused | Pick 2-3 relevant per feature |
| **Only happiness** | Satisfaction ≠ behavior | Balance attitudinal + behavioral |
| **Ignoring task success** | Missing friction points | Track completion rates |
| **No GSM process** | Metrics without purpose | Start with Goals, derive Signals |

### Anti-Patterns

- **Framework cargo cult** — Using AARRR/HEART labels without real metrics
- **Measuring everything** — Pick what matters, ignore the rest
- **No targets** — Metrics without goals are just numbers
- **Stage skipping** — Jumping to revenue before activation works
- **Averages only** — Segment metrics by cohort, source, behavior
- **Snapshot thinking** — Track trends, not just current state
