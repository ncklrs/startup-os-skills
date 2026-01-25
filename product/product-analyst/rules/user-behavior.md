---
title: User Behavior Analytics
impact: HIGH
tags: behavior, analytics, patterns, segmentation
---

## User Behavior Analytics

**Impact: HIGH**

Understanding how users actually behave — not how you think they behave — is the foundation of product insight. Behavior data reveals intent, friction, and opportunity.

### Types of Behavioral Data

| Type | What It Captures | Tools |
|------|------------------|-------|
| **Event Data** | Actions (clicks, creates, purchases) | Amplitude, Mixpanel, Segment |
| **Session Data** | Sequences and flows | Fullstory, Hotjar |
| **Engagement** | Depth and frequency | Product analytics |
| **Journey** | Cross-session paths | Journey mapping tools |
| **Heatmaps** | Where users look/click | Hotjar, Crazy Egg |
| **Recordings** | Actual user sessions | Fullstory, Logrocket |

### Behavioral Segmentation

**Segmentation Dimensions:**

| Dimension | Examples | Use Case |
|-----------|----------|----------|
| **Usage Frequency** | Daily, weekly, monthly | Identify power users |
| **Feature Adoption** | Features used, depth | Product development |
| **Lifecycle Stage** | New, activated, retained | Targeted engagement |
| **Value Tier** | Free, paid, enterprise | Monetization |
| **Behavior Pattern** | Creator, consumer, lurker | UX optimization |

**Creating Behavioral Segments:**

```
Segment: Power Users
Definition:
- Active 5+ days per week
- Use 3+ core features
- Generate content (not just consume)
- Active for 30+ days

Characteristics:
┌─────────────────────────────────────────────────────────┐
│ Metric               │ Power Users │ Regular Users     │
├─────────────────────────────────────────────────────────┤
│ % of user base       │    8%       │     92%           │
│ Sessions/week        │   12.4      │      2.1          │
│ Features used        │    6.2      │      2.3          │
│ Content created/week │   15.0      │      1.8          │
│ Retention (D90)      │   85%       │     32%           │
│ LTV                  │  $420       │     $85           │
└─────────────────────────────────────────────────────────┘

Insight: Power users are 5x more valuable
Question: How do we create more power users?
```

### Behavioral Pattern Analysis

**1. Path Analysis**

```
Most Common Paths to First Purchase:

Path 1 (35% of purchases):
Homepage → Product Page → Add to Cart → Purchase

Path 2 (25% of purchases):
Search → Product Page → Wishlist → Return → Purchase

Path 3 (18% of purchases):
Category → Filter → Product → Compare → Purchase

Path 4 (12% of purchases):
Email Link → Product Page → Purchase

Insight: Direct purchase path (Path 1) converts fastest
Opportunity: Reduce steps for Path 2/3 users
```

**2. Sequence Analysis**

```
What do retained users do in Week 1?

Retained (D30 > 0) vs Churned users:
┌────────────────────────────────────────────────────────┐
│ W1 Action           │ Retained │ Churned │ Difference │
├────────────────────────────────────────────────────────┤
│ Completed tutorial  │   78%    │   35%   │   +43pp    │
│ Created first item  │   85%    │   42%   │   +43pp    │
│ Invited team member │   52%    │   12%   │   +40pp    │
│ Used mobile app     │   65%    │   38%   │   +27pp    │
│ Set up integration  │   42%    │   18%   │   +24pp    │
└────────────────────────────────────────────────────────┘

Activation checklist priority:
1. Completed tutorial (biggest gap)
2. Created first item
3. Invited team member
```

**3. Frequency Analysis**

```
User Activity Distribution:
┌────────────────────────────────────────────────────────┐
│ Sessions/Week │ % Users │ Retention │ LTV            │
├────────────────────────────────────────────────────────┤
│ 0 (dormant)   │   25%   │   N/A     │   $0           │
│ 1-2 (light)   │   40%   │   22%     │   $45          │
│ 3-5 (regular) │   25%   │   55%     │   $120         │
│ 6+ (heavy)    │   10%   │   82%     │   $340         │
└────────────────────────────────────────────────────────┘

Target: Move light users to regular
```

### Behavioral Triggers

**Identifying Critical Moments:**

| Trigger Type | Example | Response |
|--------------|---------|----------|
| **First-time** | First login, first action | Guided onboarding |
| **Achievement** | Milestone reached | Celebration + next step |
| **Inactivity** | No action in X days | Re-engagement email |
| **Risk signal** | Decrease in usage | Proactive outreach |
| **Opportunity** | Feature almost used | Contextual nudge |

**Behavioral Trigger Implementation:**

```
Trigger: Inactivity Warning

Condition:
- User was active (3+ sessions/week)
- Now inactive (0 sessions in 7 days)
- Has valuable content in account

Action:
- Send "We miss you" email at day 7
- Show "what's new" at next login
- Log re-engagement_triggered event

Measurement:
- Re-engagement rate: 18%
- Resurrection rate: 12%
```

### Session Analysis

**Session Metrics:**

| Metric | Definition | Target |
|--------|------------|--------|
| **Session Duration** | Time from start to end | Depends on product |
| **Actions/Session** | Events in session | 8-15 for engaged |
| **Pages/Session** | Screens visited | 4-8 typical |
| **Session Depth** | Features touched | 2+ for value |
| **Bounce Rate** | Single-page sessions | <30% for core flows |

**Session Recording Analysis:**

```
Session Review Protocol:
1. Watch 10-20 sessions per week
2. Focus on:
   - Drop-off points (where users quit)
   - Confusion signals (rage clicks, back navigation)
   - Success patterns (smooth completion)
   - Unexpected behaviors (workarounds)

Document:
- Friction point and timestamp
- User segment
- Frequency (1 user or pattern?)
- Potential fix
- Priority (impact × frequency)
```

### Good vs Bad Behavior Analysis

**Good: Segmented, Actionable**

```
Analysis: Feature X Usage Patterns

Approach:
1. Segmented by user type (new vs returning)
2. Tracked full usage funnel
3. Compared high vs low engagers
4. Correlated with outcomes

Findings:
┌─────────────────────────────────────────────────────────┐
│ Behavior                  │ High Retain │ Low Retain   │
├─────────────────────────────────────────────────────────┤
│ Used Feature X in W1      │    72%      │    28%       │
│ Used Feature X 3+ times   │    65%      │    12%       │
│ Combined with Feature Y   │    58%      │     8%       │
└─────────────────────────────────────────────────────────┘

Insight: Feature X + Y combination predicts retention
Action: Prompt Feature Y users to try Feature X

Result: +15% feature adoption, +8% D30 retention
```

**Bad: Aggregate, No Action**

```
Analysis: User Behavior Report

Findings:
- Average session duration: 4.2 minutes
- Average actions per session: 6.8
- Most clicked: Dashboard

Problems:
- No segmentation
- No comparison to outcome
- Averages hide patterns
- No actionable insight
- "Most clicked" isn't insight
```

### Predictive Behavior Signals

**Churn Prediction Signals:**

```
High-Risk Indicators:
┌─────────────────────────────────────────────────────────┐
│ Signal                   │ Weight │ Threshold          │
├─────────────────────────────────────────────────────────┤
│ Session frequency drop   │  0.35  │ -50% vs avg        │
│ Feature usage decline    │  0.25  │ -30% features      │
│ Support tickets up       │  0.20  │ 2+ in 30 days      │
│ Login failures           │  0.10  │ 3+ in 7 days       │
│ Billing issues           │  0.10  │ Failed payment     │
└─────────────────────────────────────────────────────────┘

Risk Score = Σ(signal × weight)
High risk: Score > 0.6
```

**Upgrade Prediction Signals:**

```
Ready-to-Upgrade Indicators:
┌─────────────────────────────────────────────────────────┐
│ Signal                   │ Indicator                   │
├─────────────────────────────────────────────────────────┤
│ Limit approaching        │ 80% of plan limit           │
│ Premium feature attempts │ 3+ clicks on locked feature │
│ Team growth              │ Inviting new members        │
│ Usage acceleration       │ +50% activity vs last month │
│ Pricing page visits      │ 2+ views in 30 days         │
└─────────────────────────────────────────────────────────┘
```

### Behavioral Analytics Tools

| Tool | Best For | Key Features |
|------|----------|--------------|
| **Amplitude** | Product analytics | Funnels, cohorts, paths |
| **Mixpanel** | Event analytics | Real-time, segmentation |
| **Fullstory** | Session replay | Recordings, heatmaps |
| **Heap** | Auto-capture | Retroactive analysis |
| **Pendo** | In-app analytics | Usage tracking, guides |
| **PostHog** | Open source | Full stack, self-hosted |

### Anti-Patterns

- **Aggregate obsession** — Averages hide the story
- **Correlation = causation** — Behavior correlates, doesn't cause
- **Recency bias** — This week's pattern ≠ trend
- **Confirmation bias** — Finding data to support decisions
- **Privacy violation** — Tracking too much, too granularly
- **Analysis without action** — Insights that don't change anything
- **Segment pollution** — Too many segments, no clear personas
- **Ignoring context** — Behavior without the "why"
