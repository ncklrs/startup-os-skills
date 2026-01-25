---
title: Commission Calculation & Tracking
impact: MEDIUM-HIGH
tags: commission, compensation, tracking, spiffs, accelerators
---

## Commission Calculation & Tracking

**Impact: MEDIUM-HIGH**

Reps trust you with their paycheck. Commission accuracy builds trust; errors destroy it. Clear rules drive behavior; ambiguous rules create disputes.

### Commission Plan Components

```
┌─────────────────────────────────────────────────────────────┐
│                    TOTAL COMPENSATION                        │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│   BASE SALARY        VARIABLE (OTE)        BONUSES          │
│      60%                 40%               (Additional)      │
│                                                              │
│   Fixed pay          Commission on         SPIFFs, MBOs,    │
│                      quota attainment      team bonuses      │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

### Standard Commission Structures

| Structure | How It Works | Best For |
|-----------|--------------|----------|
| **Linear** | Fixed % on all revenue | Simple, predictable |
| **Tiered** | % increases at thresholds | Reward overperformance |
| **Accelerators** | Higher % above quota | Drive quota attainment |
| **Decelerators** | Lower % below threshold | Prevent sandbagging |
| **Uncapped** | No maximum commission | Motivate top performers |
| **Capped** | Maximum payout limit | Budget predictability |

### Commission Calculation Example

**Plan Structure:**

```
Base Salary: $75,000
OTE: $150,000 (50/50 split)
Variable Target: $75,000
Quota: $1,000,000

Rate Structure:
- 0-80% quota: 5% commission rate
- 80-100% quota: 7.5% commission rate
- 100-120% quota: 10% commission rate (1.33x accelerator)
- >120% quota: 12% commission rate (1.6x accelerator)
```

**Calculation at $1,200,000 (120% attainment):**

```
Tier 1: $0 - $800K (80%)     = $800,000 × 5%  = $40,000
Tier 2: $800K - $1M (80-100%) = $200,000 × 7.5% = $15,000
Tier 3: $1M - $1.2M (100-120%) = $200,000 × 10% = $20,000
                                 ─────────────────────────
Total Commission:                               = $75,000

At 120% attainment, rep earns $75K (100% of variable target)
Total Comp: $75K base + $75K commission = $150K (exactly OTE)
```

### Commission Tracking Dashboard

```
┌────────────────────────────────────────────────────────────┐
│               COMMISSION TRACKING - Q1 2025                 │
├────────────────────────────────────────────────────────────┤
│ Rep: Sarah Johnson                                          │
│ Quota: $250,000        Closed: $287,500 (115%)             │
│                                                             │
│ ┌────────────────────────────────────────────────────────┐ │
│ │ Deal              Amount    Rate    Commission Status  │ │
│ ├────────────────────────────────────────────────────────┤ │
│ │ Acme Corp         $85,000   7.5%    $6,375    Paid    │ │
│ │ TechStart Inc     $62,500   7.5%    $4,688    Paid    │ │
│ │ BigCo LLC         $95,000   10%     $9,500    Pending │ │
│ │ Startup XYZ       $45,000   10%     $4,500    Pending │ │
│ └────────────────────────────────────────────────────────┘ │
│                                                             │
│ Total Earned: $25,063                                       │
│ Paid to Date: $11,063                                       │
│ Pending:      $14,000 (pays Feb 15)                        │
└────────────────────────────────────────────────────────────┘
```

### Commission Rules Matrix

| Scenario | Rule | Example |
|----------|------|---------|
| Multi-year deal | Commission on Year 1 only OR amortized | 3-year $300K = $100K commissionable |
| Discount >20% | Manager approval required | Standard rate still applies |
| Churned within 90 days | Clawback provision | Full commission returned |
| Split deal | Defined % by role | AE 60% / SDR 40% |
| Renewal | Lower rate (50% of new) | $50K renewal = $25K effective |
| Expansion | Full rate or discounted | Upsell treated as new business |
| Professional services | Excluded or reduced | Services revenue at 25% rate |

### Deal Split Scenarios

**Standard Split Configuration:**

```
New Business Deal:
├── AE (Closer): 100% OR split with SDR
├── SDR (Sourced): 20-30% of AE rate if sourced
└── SE (Supported): SPIFFs only, not commission

Expansion Deal:
├── AE (Closer): 60%
├── CSM (Owned account): 40%
└── SDR: 0% (no sourcing needed)

Partner Deal:
├── AE (Closed): 80%
├── Partner Manager: 20%
└── SDR: 0%
```

### Commission Calculation Code

```python
# Commission calculation engine
class CommissionCalculator:
    def __init__(self, plan):
        self.tiers = plan['tiers']  # [(threshold_pct, rate), ...]
        self.quota = plan['quota']

    def calculate(self, revenue):
        attainment = revenue / self.quota
        commission = 0
        remaining_revenue = revenue

        for i, (threshold, rate) in enumerate(self.tiers):
            tier_ceiling = self.quota * threshold
            if i == 0:
                tier_floor = 0
            else:
                tier_floor = self.quota * self.tiers[i-1][0]

            tier_revenue = min(remaining_revenue, tier_ceiling - tier_floor)
            tier_revenue = max(0, tier_revenue)

            commission += tier_revenue * rate
            remaining_revenue -= tier_revenue

            if remaining_revenue <= 0:
                break

        # Handle any revenue above last tier
        if remaining_revenue > 0:
            commission += remaining_revenue * self.tiers[-1][1]

        return commission

# Example usage
plan = {
    'quota': 1000000,
    'tiers': [
        (0.80, 0.05),   # 0-80%: 5%
        (1.00, 0.075),  # 80-100%: 7.5%
        (1.20, 0.10),   # 100-120%: 10%
        (float('inf'), 0.12)  # >120%: 12%
    ]
}

calc = CommissionCalculator(plan)
print(calc.calculate(1200000))  # $75,000
```

### SPIFF Program Design

| SPIFF Type | Trigger | Payout | Duration |
|------------|---------|--------|----------|
| **Product Launch** | Close new product deal | $500-$2,000 | 90 days |
| **Competitive Win** | Displace named competitor | $1,000 | Ongoing |
| **Multi-Year** | Close 2+ year deal | 10% bonus | Ongoing |
| **Fast Close** | Close within 30 days | $250 | Quarterly |
| **New Logo** | First deal with company | $500 | Ongoing |

### Commission Dispute Resolution

**Dispute Process:**

```
1. Rep submits dispute via form
   ├── Deal ID
   ├── Expected commission
   ├── Actual commission
   └── Reason for dispute

2. Sales Ops review (48 hours)
   ├── Verify deal data
   ├── Check commission rules
   └── Calculate correct amount

3. Resolution
   ├── If error found → Adjust + apologize
   ├── If rules unclear → Escalate to VP
   └── If correct → Explain with documentation

4. Communication
   └── Document decision in writing
```

### Commission Technology Stack

| Tool | Best For | Complexity |
|------|----------|------------|
| **CaptivateIQ** | Mid-market, complex plans | Medium |
| **Xactly** | Enterprise, full suite | High |
| **Spiff** | SMB, simple plans | Low |
| **Performio** | Mid-market | Medium |
| **Excel** | Startups, <20 reps | Low |
| **Custom build** | Unique requirements | High |

### Anti-Patterns

- **Unclear rules** — "Manager discretion" on important items
- **Retroactive changes** — Changing rules mid-quarter
- **Delayed payment** — Commission paid >30 days after close
- **Manual calculation** — Spreadsheet errors erode trust
- **No visibility** — Reps can't see their own calculations
- **Clawback abuse** — Excessive or unclear clawback policies
- **Cap on overperformance** — Kills motivation for top reps
- **Impossible quotas** — Setting reps up to fail
