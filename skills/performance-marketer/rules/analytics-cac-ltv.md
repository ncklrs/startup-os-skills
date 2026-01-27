---
title: CAC/LTV Analysis
impact: HIGH
tags: analytics, cac, ltv, unit-economics, metrics
---

## CAC/LTV Analysis

**Impact: HIGH**

Unit economics determine if your growth is sustainable. Great CAC/LTV ratios are the foundation of scalable businesses.

### Core Metrics

| Metric | Formula | What It Tells You |
|--------|---------|-------------------|
| **CAC** | Total Acquisition Cost ÷ New Customers | Cost to acquire one customer |
| **LTV** | ARPU × Gross Margin × Customer Lifespan | Total value of a customer |
| **LTV:CAC** | LTV ÷ CAC | Return on acquisition spend |
| **Payback** | CAC ÷ Monthly Gross Profit | Months to recover CAC |

### CAC Calculation Methods

#### Blended CAC
```
CAC = (Sales + Marketing Spend) ÷ New Customers
```

#### Fully Loaded CAC
```
CAC = (Sales + Marketing + Salaries + Tools + Overhead) ÷ New Customers
```

#### Channel CAC
```
CAC = Channel Spend ÷ Customers from Channel
```

### LTV Calculation Methods

#### Simple LTV
```
LTV = ARPU × Average Customer Lifespan (months)
```

#### Gross Margin LTV
```
LTV = ARPU × Gross Margin % × Avg Lifespan
```

#### DCF LTV (Discounted)
```
LTV = Σ (Monthly Revenue × Margin) ÷ (1 + Discount Rate)^month
```

### LTV:CAC Benchmarks

| Ratio | Assessment | Action |
|-------|------------|--------|
| <1:1 | Losing money | Stop spending, fix fundamentals |
| 1:1 - 2:1 | Barely sustainable | Improve retention or reduce CAC |
| 2:1 - 3:1 | Acceptable | Optimize, could scale cautiously |
| 3:1 - 5:1 | Healthy | Scale spending |
| 5:1+ | Under-investing | Increase spend, capture market |

### Payback Period Benchmarks

| Payback | Assessment | Context |
|---------|------------|---------|
| <3 months | Excellent | SMB, self-serve |
| 3-6 months | Very good | PLG, mid-market |
| 6-12 months | Good | Most SaaS |
| 12-18 months | Acceptable | Enterprise |
| 18+ months | Risky | High churn concern |

### CAC by Channel

| Channel | Typical CAC Range | Notes |
|---------|-------------------|-------|
| **Organic/SEO** | $10-50 | Long to build, compounds |
| **Referral** | $20-100 | Best quality, limited scale |
| **Content** | $30-150 | Builds brand, takes time |
| **Google Search** | $50-300 | High intent, competitive |
| **Meta Ads** | $40-200 | Scale, mid-intent |
| **LinkedIn Ads** | $150-600 | B2B, expensive but targeted |
| **Outbound Sales** | $500-5000 | Enterprise, high ACV |

### LTV Improvement Levers

| Lever | Impact | Tactics |
|-------|--------|---------|
| **Reduce churn** | High | Better onboarding, support, product |
| **Increase ARPU** | High | Upsells, pricing, expansion revenue |
| **Improve margins** | Medium | Reduce COGS, operational efficiency |
| **Cross-sell** | Medium | Additional products, add-ons |
| **Referrals** | Medium | Referral program, advocacy |

### CAC Reduction Levers

| Lever | Impact | Tactics |
|-------|--------|---------|
| **Improve conversion** | High | CRO, landing pages, funnel optimization |
| **Better targeting** | High | Audience refinement, lookalikes |
| **Organic growth** | Medium-High | SEO, content, community |
| **Sales efficiency** | Medium | Automation, qualification, enablement |
| **Channel mix** | Medium | Shift budget to efficient channels |

### Cohort Analysis Framework

Track cohorts to understand true LTV:

```
| Cohort    | M0  | M1  | M2  | M3  | M6  | M12 |
|-----------|-----|-----|-----|-----|-----|-----|
| Jan 2024  | 100%| 85% | 78% | 72% | 60% | 45% |
| Feb 2024  | 100%| 82% | 75% | 70% | 58% | -   |
| Mar 2024  | 100%| 88% | 80% | 74% | -   | -   |
```

### Good CAC/LTV Analysis

```
✓ Segment by acquisition channel
  → Google Search CAC: $150, LTV: $600 (4:1)
  → Meta Ads CAC: $80, LTV: $200 (2.5:1)
  → Action: Shift budget to Google Search

✓ Track cohorts over time
  → 2023 cohorts: 40% 12-month retention
  → 2024 cohorts: 55% 12-month retention
  → LTV improving due to product improvements

✓ Account for payback period
  → 8-month payback with 15-month avg lifespan
  → Healthy, can scale
```

### Bad CAC/LTV Analysis

```
✗ Blended CAC only
  → Hides that one channel is unprofitable

✗ LTV without gross margin
  → Overstates profitability

✗ Short-term LTV projections
  → Need 12+ months of data minimum

✗ Ignoring acquisition channel
  → Organic and paid customers behave differently

✗ Not updating regularly
  → Markets change, metrics drift
```

### Reporting Dashboard Metrics

| Metric | Update Frequency | Trend Direction |
|--------|-----------------|-----------------|
| CAC (blended) | Weekly | Lower is better |
| CAC (by channel) | Weekly | Lower is better |
| LTV | Monthly | Higher is better |
| LTV:CAC | Monthly | Higher is better |
| Payback (months) | Monthly | Shorter is better |
| Retention curve | Monthly | Flatter is better |
| ARPU | Monthly | Higher is better |
| Churn rate | Monthly | Lower is better |

### Anti-Patterns

- **Blended-only thinking** — Hides channel inefficiencies
- **Projecting LTV too early** — Need cohort data, not projections
- **Ignoring gross margin** — Revenue ≠ profit
- **Annual CAC, monthly LTV** — Match time periods
- **Not segmenting** — SMB vs enterprise is different
- **Ignoring payback** — Cash flow matters
- **One-time calculation** — Metrics change, update regularly
