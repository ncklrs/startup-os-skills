---
title: Customer Segmentation
impact: HIGH
tags: segmentation, targeting, personalization, analytics
---

## Customer Segmentation

**Impact: HIGH**

Treating all customers the same means being relevant to none. Segmentation powers personalization across the entire lifecycle.

### Segmentation Dimensions

| Dimension | Examples | Use For |
|-----------|----------|---------|
| **Behavioral** | Usage, features, engagement | In-product, email |
| **Demographic** | Company size, industry, role | Content, pricing |
| **Value** | MRR, LTV, tier | Resource allocation |
| **Lifecycle** | New, active, at-risk, churned | Messaging, offers |
| **Need** | Use case, problem solved | Product, positioning |

### Behavioral Segmentation

| Segment | Definition | Strategy |
|---------|------------|----------|
| **Power users** | Top 20% by usage | Advocacy, beta access, expansion |
| **Active users** | Regular, moderate usage | Deepen adoption, cross-sell |
| **Light users** | Infrequent, basic usage | Education, value discovery |
| **Dormant** | No recent activity | Re-engagement, save |
| **New** | <30 days tenure | Onboarding focus |

### Value-Based Segmentation

| Segment | Criteria | Approach |
|---------|----------|----------|
| **Enterprise** | >$50k ARR | High-touch, strategic |
| **Mid-market** | $10-50k ARR | Hybrid, scaled success |
| **SMB** | $1-10k ARR | Tech-touch, automated |
| **Self-serve** | <$1k ARR | Product-led, community |

### Lifecycle Segmentation

| Stage | Tenure | Behavior | Focus |
|-------|--------|----------|-------|
| **Onboarding** | 0-30 days | Learning | Activation |
| **Adopting** | 30-90 days | Growing usage | Habit formation |
| **Established** | 90-365 days | Consistent | Retention + expansion |
| **Mature** | 365+ days | Stable | Advocacy + renewals |

### Health-Based Segmentation

| Health | Score | Action Priority |
|--------|-------|-----------------|
| **Champions** | 80-100 | Expansion, advocacy |
| **Healthy** | 60-79 | Maintain, grow |
| **Neutral** | 40-59 | Proactive engagement |
| **At-risk** | 20-39 | Intervention |
| **Critical** | 0-19 | Save or transition |

### Good Segmentation

```
✓ Actionable
  → Each segment has a distinct strategy
  → Clear "so what" for each

✓ Measurable
  → Can track segment membership
  → Can measure segment performance

✓ Mutually exclusive
  → Customer belongs to one segment
  → No overlap confusion

✓ Dynamic
  → Segments update as behavior changes
  → Not frozen at signup

✓ Right granularity
  → Enough to personalize, not too many to manage
  → 5-10 segments typical
```

### Bad Segmentation

```
✗ Demographic only
  → "Small companies" ignores usage patterns
  → Behavior matters more

✗ Too many segments
  → 50 segments = no capacity to act differently
  → Complexity without value

✗ Static assignment
  → "Enterprise" customer at signup stays enterprise
  → Even if they downgrade to SMB usage

✗ No strategy per segment
  → Segments exist but treatment is identical
  → Why bother segmenting?

✗ Gut-based
  → "I think they're important"
  → Data should drive classification
```

### RFM Segmentation

Classic framework adapted for SaaS:

| Factor | Meaning | Scoring |
|--------|---------|---------|
| **Recency** | When last active | 1-5 (5 = most recent) |
| **Frequency** | How often active | 1-5 (5 = most frequent) |
| **Monetary** | Revenue/value | 1-5 (5 = highest value) |

| RFM Score | Segment | Strategy |
|-----------|---------|----------|
| 555 | Champions | Advocacy, VIP treatment |
| 444-554 | Loyal | Upsell, cross-sell |
| 433-443 | Promising | Develop, engage |
| 322-333 | At-risk | Re-engage, special offers |
| 111-222 | Dormant | Win-back or sunset |

### Segment-Specific Strategies

| Segment | Email Frequency | Content Type | CSM Touch |
|---------|-----------------|--------------|-----------|
| **Champions** | 2-3x/month | Exclusive, early access | Monthly call |
| **Active** | Weekly | Tips, features | Quarterly |
| **Light** | 2x/week | Education, value | As needed |
| **At-risk** | Daily (campaign) | Help, offers | Immediate |
| **Dormant** | Weekly (re-engage) | Win-back | One-time |

### Building Segments (Technical)

| Source | Data Points |
|--------|-------------|
| **Product** | Logins, features used, depth, time |
| **Billing** | MRR, plan, payment history |
| **Support** | Tickets, NPS, sentiment |
| **Sales** | Account type, close date, notes |
| **Marketing** | Email engagement, event attendance |

### Segment Queries Example

```sql
-- Power Users
SELECT customer_id
FROM usage_data
WHERE logins_30d >= 20
  AND features_used >= 5
  AND depth_score >= 80

-- At-Risk
SELECT customer_id
FROM customer_health
WHERE health_score < 40
  AND tenure_days > 90
  AND churn_predicted > 0.5

-- Expansion Ready
SELECT customer_id
FROM customers
WHERE health_score >= 70
  AND usage_pct_of_limit >= 80
  AND nps_score >= 8
```

### Segment Metrics Dashboard

| Metric | By Segment |
|--------|------------|
| **Count** | Customers in each segment |
| **% of total** | Distribution |
| **MRR** | Revenue by segment |
| **Churn rate** | Risk by segment |
| **NPS** | Satisfaction by segment |
| **Expansion rate** | Growth by segment |
| **Movement** | Transitions between segments |

### Segment Transitions to Watch

| Transition | Signal | Action |
|------------|--------|--------|
| Active → Light | Declining engagement | Proactive outreach |
| Light → Dormant | Abandonment risk | Re-engagement campaign |
| Healthy → At-risk | Health score drop | Intervention |
| Active → Champion | Growing engagement | Advocacy ask |
| At-risk → Healthy | Recovery | Celebrate, reinforce |

### Personalization by Segment

| Element | How to Personalize |
|---------|-------------------|
| **Email content** | Tips vs education vs advocacy asks |
| **Email frequency** | High engagement = more, low = less |
| **In-app messaging** | Feature tips vs basic help |
| **Support priority** | By value, by health |
| **CSM allocation** | High-value = dedicated |
| **Renewal offers** | By health, by expansion potential |

### Anti-Patterns

- **One size fits all** — Same treatment regardless of segment
- **Demographic-only** — Ignores actual behavior
- **Too complex** — 50 segments nobody can execute against
- **Static** — Never updated as behavior changes
- **No measurement** — Can't track segment performance
- **Siloed** — Each team has different segmentation
- **Over-indexing on value** — Low MRR ≠ low potential
