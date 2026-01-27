---
title: Customer Segmentation & Tier Scoring
impact: MEDIUM-HIGH
tags: segmentation, tier-scoring, customer-tiers, behavioral-clustering
---

## Customer Segmentation & Tier Scoring

**Impact: MEDIUM-HIGH**

Not all customers are equal — and treating them equally means over-investing in some and under-investing in others. Effective segmentation enables right-sized engagement models, focused resources, and segment-specific success strategies. Tier scoring determines service levels.

### The Segmentation Framework

```
┌──────────────────────────────────────────────────────────────────┐
│                   SEGMENTATION DIMENSIONS                        │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  VALUE                    HEALTH                  POTENTIAL      │
│  (Current Worth)          (Current State)         (Future Worth) │
│                                                                  │
│  • ARR / MRR              • Health score          • Growth rate  │
│  • Lifetime value         • Engagement level      • Expansion    │
│  • Contract length        • Risk tier               capacity     │
│  • Payment history        • NPS/Sentiment         • Strategic    │
│                                                                  │
│                          ↓                                       │
│                                                                  │
│                 CUSTOMER TIER ASSIGNMENT                         │
│                                                                  │
│                 Enterprise │ Growth │ Scale │ Tech-touch        │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Value-Based Segmentation

| Tier | ARR Range | % of Customers | % of ARR | Engagement Model |
|------|-----------|----------------|----------|------------------|
| **Enterprise** | >$100K | 5-10% | 40-50% | High-touch, named CSM |
| **Mid-Market** | $25K-$100K | 15-25% | 25-35% | Pooled CSM, proactive |
| **SMB** | $5K-$25K | 30-40% | 15-25% | Scaled, digital-first |
| **Starter** | <$5K | 30-40% | 5-10% | Tech-touch, self-serve |

### Tier Scoring Model

```
Customer Tier Score Calculation

TIER SCORE = (Value Score × 0.4) + (Potential Score × 0.35) + (Strategic Score × 0.25)

Value Score Components (0-100):
├── ARR percentile (50%)
├── Contract length (25%)
└── Payment reliability (25%)

Potential Score Components (0-100):
├── Growth trajectory (40%)
├── Seat expansion capacity (30%)
└── Product fit depth (30%)

Strategic Score Components (0-100):
├── Brand recognition (35%)
├── Reference potential (35%)
└── Market influence (30%)

Tier Assignment:
├── Tier 1 (Enterprise): Score 80-100
├── Tier 2 (Growth):     Score 60-79
├── Tier 3 (Scale):      Score 40-59
└── Tier 4 (Tech-touch): Score 0-39
```

### Good Tier Assignment

```
Customer Tier Assessment: TechCorp Inc.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

VALUE SCORE: 72/100
├── ARR: $65,000 (68th percentile)        → 68 pts
├── Contract: 2-year agreement            → 80 pts
└── Payment: Always on time               → 100 pts
Weighted: 72

POTENTIAL SCORE: 85/100
├── Growth: 25% user growth last year     → 90 pts
├── Expansion: Using 40% of seats         → 75 pts
└── Product fit: 8/10 use cases match     → 80 pts
Weighted: 85

STRATEGIC SCORE: 68/100
├── Brand: Known regional player          → 60 pts
├── Reference: Willing, used once         → 75 pts
└── Influence: 500 LinkedIn followers     → 70 pts
Weighted: 68

TOTAL TIER SCORE: 75.3

Tier Assignment: TIER 2 (Growth)
Engagement Model: Pooled CSM with proactive touchpoints
Rationale: Strong potential for expansion, moderate current value

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Bad Tier Assignment

```
Customer Tier: Enterprise

Reason: They asked for a dedicated CSM.

Problems:
✗ No objective criteria
✗ Based on customer request, not value
✗ No scoring methodology
✗ No potential assessment
✗ No strategic consideration
✗ Will lead to misallocated resources
```

### Behavioral Segmentation

| Segment | Behavior Pattern | Typical Needs | Engagement Focus |
|---------|------------------|---------------|------------------|
| **Champions** | High usage, high NPS, advocates | Expansion, recognition | Advocacy programs |
| **Power Users** | Heavy usage, feature depth | Advanced training | Feature betas |
| **Steady State** | Consistent, moderate usage | Efficiency, stability | Check-ins, optimization |
| **Light Touch** | Minimal engagement, still renews | Self-service, cost focus | Digital nurture |
| **Expanding** | Growing seats/usage | Onboarding, enablement | Growth support |
| **Declining** | Usage trending down | Intervention, value proof | Proactive outreach |
| **At-Risk** | Multiple churn signals | Rescue, retention | Save playbooks |

### Segment-Specific Success Strategies

```
ENTERPRISE SEGMENT ($100K+ ARR)

Engagement Model:
├── Named Strategic CSM (1:10-15 ratio)
├── Dedicated Executive Sponsor
├── Quarterly Business Reviews
├── Annual Strategic Planning
└── Direct access to product leadership

Success Activities:
├── Monthly strategic check-ins
├── Bi-weekly operational reviews
├── Custom success plans
├── Early access to roadmap
└── Executive-level escalation path

Metrics Focus:
├── Value realization / ROI
├── Stakeholder satisfaction
├── Strategic alignment
├── Expansion pipeline
└── Reference/advocacy activity

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

TECH-TOUCH SEGMENT (<$5K ARR)

Engagement Model:
├── Automated, digital-first
├── Community-based support
├── Self-service resources
└── Exception-based human touch

Success Activities:
├── Automated onboarding sequences
├── In-app guidance and tutorials
├── Community forum engagement
├── Triggered outreach (risk, expansion)
└── Scaled webinars and office hours

Metrics Focus:
├── Activation rate
├── Feature adoption
├── Support ticket volume
├── Self-service resolution
└── Upgrade conversion rate
```

### Customer Matrix: Value vs Health

```
                    HIGH VALUE
                        │
    ┌───────────────────┼───────────────────┐
    │                   │                   │
    │   AT-RISK         │   CHAMPIONS       │
    │   HIGH VALUE      │   HIGH VALUE      │
    │                   │                   │
    │   Strategy:       │   Strategy:       │
    │   Save & retain   │   Expand & grow   │
    │   Executive focus │   Advocacy focus  │
    │                   │                   │
────┼───────────────────┼───────────────────┼────
LOW │                   │                   │ HIGH
HEALTH                  │                   │ HEALTH
────┼───────────────────┼───────────────────┼────
    │                   │                   │
    │   AT-RISK         │   HEALTHY         │
    │   LOW VALUE       │   LOW VALUE       │
    │                   │                   │
    │   Strategy:       │   Strategy:       │
    │   Evaluate ROI    │   Self-serve      │
    │   Tech-touch save │   Upgrade path    │
    │                   │                   │
    └───────────────────┼───────────────────┘
                        │
                   LOW VALUE
```

### Segment Migration Tracking

| From Tier | To Tier | Trigger | Action |
|-----------|---------|---------|--------|
| SMB → Mid-Market | ARR >$25K | Auto-upgrade | Assign CSM |
| Mid-Market → Enterprise | ARR >$100K | Manual review | Strategic CSM assignment |
| Any → At-Risk | Health <40 | Auto-flag | Escalation playbook |
| At-Risk → Healthy | Health >60 for 60 days | Auto-restore | Return to normal model |
| Declining → Churned | Cancellation | Manual process | Win-back eligibility |

### Resource Allocation by Segment

| Resource | Enterprise | Mid-Market | SMB | Tech-Touch |
|----------|------------|------------|-----|------------|
| CSM Ratio | 1:10-15 | 1:30-50 | 1:100-200 | 1:1000+ |
| QBR Frequency | Quarterly | Semi-annual | Annual | None |
| Proactive Outreach | Monthly | Bi-monthly | Quarterly | Triggered only |
| Executive Access | Direct | Escalation | None | None |
| Custom Success Plan | Yes | Template | Self-service | None |
| Priority Support | Yes | Enhanced | Standard | Community |

### Segmentation Dashboard

```
Segmentation Overview

┌─────────────────────────────────────────────────────────────────┐
│  TIER DISTRIBUTION                                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Tier        Customers    ARR         Health Avg   NRR         │
│  ─────────────────────────────────────────────────────────────  │
│  Enterprise      48       $9.8M       78           125%        │
│  Mid-Market     156       $8.2M       72           112%        │
│  SMB            187       $4.8M       68           98%         │
│  Tech-Touch     412       $2.2M       62           92%         │
│                                                                 │
│  Total          803       $25.0M      68           108%        │
│                                                                 │
├─────────────────────────────────────────────────────────────────┤
│  TIER MOVEMENT (Last Quarter)                                   │
│                                                                 │
│  ↑ Upgraded:    34 customers (+$1.2M ARR impact)               │
│  ↓ Downgraded:  12 customers (-$380K ARR impact)               │
│  → Churned:     28 customers (-$520K ARR impact)               │
│  ★ New:         67 customers (+$890K ARR impact)               │
│                                                                 │
├─────────────────────────────────────────────────────────────────┤
│  TIER-SPECIFIC ALERTS                                           │
│                                                                 │
│  Enterprise: 2 accounts at-risk (need exec attention)          │
│  Mid-Market: 8 accounts approaching Enterprise threshold       │
│  SMB: 15 accounts declining, intervention needed               │
│  Tech-Touch: Upgrade candidates identified (12 accounts)       │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Segmentation Implementation Checklist

```
□ Segment Definition
  □ Clear criteria for each tier
  □ Scoring methodology documented
  □ Thresholds validated against data
  □ Edge case handling defined

□ Data Requirements
  □ Value metrics available
  □ Potential indicators tracked
  □ Strategic scoring inputs defined
  □ Automated calculation possible

□ Engagement Models
  □ CSM ratios defined per tier
  □ Touchpoint cadence specified
  □ Resource allocation approved
  □ Escalation paths documented

□ Migration Rules
  □ Upgrade triggers defined
  □ Downgrade criteria specified
  □ Review process for changes
  □ Customer communication plan

□ Technology Setup
  □ Tier field in CRM
  □ Automated tier calculation
  □ CSM assignment automation
  □ Reporting by segment

□ Team Readiness
  □ CSMs understand segment strategies
  □ Playbooks exist per segment
  □ Training completed
  □ Metrics tracked by segment
```

### Anti-Patterns

- **ARR-only tiers** — Ignoring potential and strategic value
- **Manual assignment** — Subjective, inconsistent tiering
- **Static segmentation** — Not updating as customers change
- **One-size engagement** — Same model regardless of tier
- **Segment leakage** — Enterprise service for SMB pricing
- **Ignoring potential** — Only looking at current value
- **No migration path** — Customers stuck in initial tier
- **Resource mismatch** — High-touch for low-value, or vice versa
