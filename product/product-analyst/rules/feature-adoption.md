---
title: Feature Adoption Tracking
impact: HIGH
tags: feature, adoption, usage, product-analytics
---

## Feature Adoption Tracking

**Impact: HIGH**

Shipping features is easy. Getting users to adopt them is hard. Track adoption systematically to understand what's working and where to invest.

### The Feature Adoption Lifecycle

```
                Awareness → Trial → Adoption → Habit → Advocacy
                    │         │        │         │         │
                    ▼         ▼        ▼         ▼         ▼
                "Saw it"  "Tried it" "Use it"  "Need it"  "Love it"
                    │         │        │         │         │
Metrics:        Exposure   First Use  Regular   Power    Referral
                Rate       Rate       Usage     Usage     Rate
```

### Core Feature Adoption Metrics

| Metric | Calculation | Good Target |
|--------|-------------|-------------|
| **Awareness Rate** | Users who saw feature / Total eligible users | >80% |
| **Trial Rate** | Users who tried feature / Users aware | >40% |
| **Adoption Rate** | Regular users / Users who tried | >50% |
| **Feature DAU** | Daily active users of feature | Depends |
| **Feature Breadth** | % of user base using feature weekly | >30% for core |
| **Feature Depth** | Actions/session using feature | Growing |
| **Time to Adopt** | Days from signup to regular use | <14 days |

### Feature Adoption Framework

**Step 1: Define What "Adopted" Means**

```
Feature: Collaboration Comments

NOT Adopted:
- Saw comments feature (awareness only)
- Left one comment ever (trial only)

Adopted:
- Left 3+ comments in 2 different weeks
- Received 2+ replies to comments
- Comments are part of regular workflow
```

**Step 2: Build the Adoption Funnel**

```
Eligible Users          1,000    100%
   │
   ▼ Saw feature
Aware                     820     82%
   │
   ▼ Clicked/opened
Explored                  410     41%
   │
   ▼ Completed first use
Tried                     285     28.5%
   │
   ▼ Used 3+ times
Activated                 170     17%
   │
   ▼ Regular weekly use
Adopted                    95      9.5%
   │
   ▼ Daily/power use
Power User                 28      2.8%
```

**Step 3: Measure by Cohort**

```
Feature launched: March 1

Adoption rate by signup cohort:
┌────────────────────────────────────────────┐
│ Signup Cohort │ 30-Day Adoption Rate       │
├────────────────────────────────────────────┤
│ Pre-launch    │    8% (discovered later)   │
│ March W1      │   12% (early exposure)     │
│ March W2      │   18% (improved UX)        │
│ March W3      │   22% (onboarding added)   │
│ March W4      │   25% (tutorial added)     │
└────────────────────────────────────────────┘

Insight: Each improvement increases adoption
```

### Feature Usage Segmentation

**Usage Depth Tiers:**

| Tier | Definition | % of Feature Users |
|------|------------|-------------------|
| **Power** | Daily use, advanced actions | 5-10% |
| **Regular** | Weekly use, core actions | 20-30% |
| **Occasional** | Monthly use, basic actions | 30-40% |
| **Trial** | 1-2 uses total | 25-40% |

**Segment Analysis:**

```
Feature: Advanced Analytics

User Segment Analysis:
┌─────────────────────────────────────────────────────────┐
│ User Type    │ Adoption │ Depth      │ Retention Impact│
├─────────────────────────────────────────────────────────┤
│ Enterprise   │   68%    │ High       │ +25% retention  │
│ Mid-market   │   42%    │ Medium     │ +12% retention  │
│ SMB          │   15%    │ Low        │ +5% retention   │
│ Free tier    │    3%    │ Very low   │ +2% retention   │
└─────────────────────────────────────────────────────────┘

Insight: Feature is enterprise-focused, not relevant to SMB
Action: Gate feature for SMB, or simplify for their needs
```

### Feature Success Scorecard

| Dimension | Metric | Target | Status |
|-----------|--------|--------|--------|
| **Reach** | % of users who tried | 40% | 28% |
| **Adoption** | % of triers who adopted | 50% | 35% |
| **Engagement** | Actions/week by adopters | 5 | 3.2 |
| **Retention** | Feature user retention vs non | +10% | +8% |
| **Value** | NPS of feature users | 50 | 42 |
| **Revenue** | Conversion impact | +5% | +3% |

**Overall Score:** Needs improvement (4/6 under target)

### Feature Adoption vs Retention Impact

```
Question: Is this feature worth keeping?

Feature Impact Matrix:
                        Low Retention Impact    High Retention Impact
                        ──────────────────────────────────────────────
High Adoption           │ SIMPLIFY             │ INVEST
                        │ Popular but not      │ Core feature,
                        │ sticky. Reduce cost  │ double down
                        │                      │
Low Adoption            │ SUNSET               │ EXPOSE
                        │ Nobody uses,         │ Valuable but hidden.
                        │ nobody misses        │ Improve discovery
                        ──────────────────────────────────────────────
```

### Good vs Bad Feature Tracking

**Good: Complete Picture**
```
Feature: Smart Scheduling

Tracking implemented:
├── Awareness events
│   ├── smart_schedule_banner_shown
│   ├── smart_schedule_tooltip_shown
│   └── smart_schedule_menu_seen
├── Trial events
│   ├── smart_schedule_clicked
│   ├── smart_schedule_first_created
│   └── smart_schedule_preview_viewed
├── Adoption events
│   ├── smart_schedule_created (with count property)
│   ├── smart_schedule_accepted
│   └── smart_schedule_modified
└── Value events
    ├── smart_schedule_conflict_resolved
    └── smart_schedule_time_saved (calculated)

Dashboard includes:
- Adoption funnel
- Cohort adoption curves
- Segment breakdown
- Retention impact
- Feature health score
```

**Bad: Basic Counting**
```
Feature: Smart Scheduling

Tracking implemented:
- smart_schedule_used (single event)

Problems:
- Can't distinguish trial vs adoption
- No awareness tracking
- No segment analysis
- No value measurement
- No retention correlation
```

### Feature Launch Measurement Plan

**Pre-Launch:**
1. Define adoption criteria
2. Instrument all funnel events
3. Set success targets
4. Build dashboard
5. Establish baseline (if applicable)

**Launch Week:**
```
Day 1-3: Awareness check
- Are users seeing the feature?
- Is discovery working?

Day 3-7: Trial check
- Are aware users trying it?
- What's the drop-off point?

Day 7-14: Early adoption
- Are triers coming back?
- What patterns emerge?
```

**Post-Launch (30/60/90 days):**
```
Monthly Review:
┌─────────────────────────────────────────────────────────┐
│ Metric              │ Target │ Day 30 │ Day 60 │ Day 90│
├─────────────────────────────────────────────────────────┤
│ Adoption rate       │  25%   │  12%   │  18%   │  22%  │
│ Weekly active users │ 1,000  │  400   │  750   │  920  │
│ Retention impact    │  +10%  │   +4%  │   +7%  │   +9% │
│ User satisfaction   │  4.2   │   3.8  │   4.0  │   4.1 │
└─────────────────────────────────────────────────────────┘
```

### Feature Sunset Criteria

When to consider sunsetting:

| Signal | Threshold | Action |
|--------|-----------|--------|
| **Adoption** | <5% after 6 months | Sunset or pivot |
| **Retention impact** | <2% difference | Low priority |
| **Maintenance cost** | High, growing | Evaluate ROI |
| **User complaints** | >complaints than praise | Investigate or sunset |
| **Strategic fit** | Off-roadmap | Planned deprecation |

### Anti-Patterns

- **Ship and forget** — No measurement plan = no learning
- **Counting clicks** — Clicks ≠ adoption, measure meaningful use
- **Ignoring non-users** — Why didn't they try? That's data too
- **Universal metrics** — Different features need different criteria
- **Short windows** — Features need 30-90 days to reach adoption
- **No control group** — Can't measure impact without comparison
- **Feature bloat** — More features ≠ better product
- **Vanity features** — Building for press releases, not users
