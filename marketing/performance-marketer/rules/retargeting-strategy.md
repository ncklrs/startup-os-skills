---
title: Retargeting Strategy
impact: MEDIUM-HIGH
tags: retargeting, remarketing, audiences, funnel
---

## Retargeting Strategy

**Impact: MEDIUM-HIGH**

Retargeting converts warm audiences at 3-10x the rate of cold. It's your most efficient spend—when done right.

### Retargeting Funnel

```
┌─────────────────────────────────────────────────────────┐
│                    ALL VISITORS                         │
│  ┌───────────────────────────────────────────────────┐  │
│  │             Homepage Visitors (30 days)           │  │
│  │  ┌─────────────────────────────────────────────┐  │  │
│  │  │        Feature Page Visitors (14 days)      │  │  │
│  │  │  ┌───────────────────────────────────────┐  │  │  │
│  │  │  │      Pricing Page Visitors (7 days)   │  │  │  │
│  │  │  │  ┌─────────────────────────────────┐  │  │  │  │
│  │  │  │  │   Cart Abandoners (3 days)      │  │  │  │  │
│  │  │  │  │  ┌───────────────────────────┐  │  │  │  │  │
│  │  │  │  │  │ Trial Starters (7 days)   │  │  │  │  │  │
│  │  │  │  │  └───────────────────────────┘  │  │  │  │  │
│  │  │  │  └─────────────────────────────────┘  │  │  │  │
│  │  │  └───────────────────────────────────────┘  │  │  │
│  │  └─────────────────────────────────────────────┘  │  │
│  └───────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────┘
          Higher Intent = More Valuable = Bid Higher
```

### Audience Segments

| Segment | Window | Intent | Bid Modifier |
|---------|--------|--------|--------------|
| Cart abandoners | 1-3 days | Very High | +50-100% |
| Pricing page | 1-7 days | High | +30-50% |
| Feature pages | 7-14 days | Medium-High | +20-30% |
| Blog readers | 14-30 days | Medium | Baseline |
| Homepage bounces | 7-14 days | Low | -20-30% |
| Past purchasers | 30-90 days | Upsell | +20-40% |

### Recency Strategy

| Time Since Visit | Message | Urgency |
|------------------|---------|---------|
| 0-24 hours | Continue where you left off | High |
| 1-3 days | Still thinking about it? | Medium-High |
| 3-7 days | Don't miss out | Medium |
| 7-14 days | We've got something new | Low |
| 14-30 days | We miss you / What's new | Re-engagement |
| 30+ days | Major announcement / Offer | Win-back |

### Sequential Messaging

```
Day 1-2: Reminder
"You left something behind"
→ Product/feature they viewed

Day 3-5: Social Proof
"Join 10,000+ teams using [Product]"
→ Testimonials, case studies

Day 6-10: Objection Handler
"Have questions? We've got answers"
→ FAQ, comparison, support

Day 11-14: Incentive
"Your exclusive offer expires soon"
→ Discount, extended trial, bonus
```

### Platform-Specific Setup

| Platform | Audience Source | Minimum Size |
|----------|----------------|--------------|
| **Meta** | Pixel, email list, video viewers | 100 |
| **Google** | GA4, YouTube, customer match | 100-1,000 |
| **LinkedIn** | Insight Tag, email list, company list | 300 |
| **Twitter/X** | Pixel, email list, followers | 500 |

### Exclusion Strategy

Always exclude:
| Exclude | From | Why |
|---------|------|-----|
| Purchasers | Acquisition campaigns | Already converted |
| Recent converts | 7-14 days | Give them time |
| Unsubscribes | Email-based audiences | They opted out |
| Churned customers | Trial conversion campaigns | Different message needed |
| Employees | All campaigns | Wasted spend |

### Frequency Capping

| Platform | Recommended Cap | Notes |
|----------|-----------------|-------|
| **Meta** | 3-5 per week | Per ad set |
| **Google Display** | 5-7 per day | Per campaign |
| **LinkedIn** | 3-5 per week | Per campaign |
| **General** | Max 2x per day | User experience |

### Good Retargeting

```
✓ Segmented by intent
  → Pricing page visitors get different message than blog readers

✓ Sequential messaging
  → Story evolves over time, not same ad repeatedly

✓ Frequency capped
  → 3-5 impressions per week max

✓ Exclusions in place
  → Customers excluded from acquisition

✓ Dynamic creative
  → Show products/features they viewed
```

### Bad Retargeting

```
✗ Everyone in one audience
  → Cart abandoners need different message than homepage bouncers

✗ Same ad for 30 days
  → Ad fatigue, annoyance, brand damage

✗ No frequency cap
  → Stalker ads damage brand

✗ No recency windows
  → Showing ads 60 days later is wasted spend

✗ Retargeting customers with acquisition ads
  → "Sign up for free trial" to paying customers
```

### Dynamic Retargeting

Show users the specific products/content they viewed:

| Element | Implementation |
|---------|----------------|
| **Product catalog** | Upload to platform (Meta, Google) |
| **Event tracking** | View content, add to cart events |
| **Template** | Dynamic ad template with placeholders |
| **Recommendation** | Similar/complementary products |

### Cross-Platform Retargeting

```
User visits website (Google Ads)
    ↓
Captured by all pixels (Meta, LinkedIn, Google)
    ↓
Sees retargeting on Meta (social browsing)
    ↓
Sees retargeting on YouTube (video content)
    ↓
Returns via Google Search ad
    ↓
Converts
```

### Retargeting Budget Split

| Segment | % of Retargeting Budget |
|---------|------------------------|
| Cart/form abandoners | 30-40% |
| Pricing page visitors | 20-30% |
| High-intent pages | 15-25% |
| General site visitors | 10-15% |
| Win-back campaigns | 5-10% |

### Measurement

| Metric | Benchmark | Target |
|--------|-----------|--------|
| **CTR** | 0.5-1% | 1.5%+ |
| **CVR** | 2-5% | 8%+ |
| **ROAS** | 3x | 5x+ |
| **Frequency** | <3/week | <2/week |
| **CPM** | Varies | Track trend |

### Anti-Patterns

- **No segmentation** — All visitors treated the same
- **No frequency cap** — Creepy, annoying, wasteful
- **No exclusions** — Advertising to customers
- **Static creative** — Same ad for weeks
- **Too long windows** — 60+ day audiences are cold again
- **Ignoring iOS changes** — Server-side tracking needed
- **No sequential messaging** — Miss opportunity to build story
- **Retargeting only** — Need cold traffic to retarget
