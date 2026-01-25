---
title: Defining Your North Star Metric
impact: CRITICAL
tags: metrics, strategy, north-star, kpi
---

## Defining Your North Star Metric

**Impact: CRITICAL**

Your North Star Metric (NSM) is the single metric that best captures the core value your product delivers to customers. Get this right and alignment follows.

### What Makes a Good North Star

**A North Star Metric must:**
1. Measure value delivered to customers (not just activity)
2. Be a leading indicator of revenue
3. Be measurable and movable
4. Be understandable across the company
5. Connect to your product's core purpose

### North Star Selection Framework

| Factor | Question | Good Sign |
|--------|----------|-----------|
| **Value** | Does this reflect customer value? | Users would agree it matters |
| **Growth** | Does improving this grow the business? | Correlates with revenue |
| **Focus** | Does this guide prioritization? | Teams can rally around it |
| **Measurable** | Can we track this reliably? | Daily/weekly updates possible |
| **Controllable** | Can our product actions influence this? | Clear input metrics exist |

### Examples by Business Model

| Business Type | North Star Metric | Why It Works |
|--------------|-------------------|--------------|
| **Slack** | Daily Active Users sending messages | Measures communication value |
| **Airbnb** | Nights booked | Core value exchange |
| **Spotify** | Time spent listening | Engagement = value delivered |
| **Shopify** | GMV (Gross Merchandise Value) | Merchant success = Shopify success |
| **Notion** | Weekly active teams | Collaboration value |
| **Zoom** | Weekly meeting minutes | Usage = value |
| **HubSpot** | Weekly active teams using 2+ hubs | Platform adoption = stickiness |

### North Star + Input Metrics

Your NSM doesn't exist alone. Build a metrics tree:

```
                    ┌─────────────────────────┐
                    │   NORTH STAR METRIC     │
                    │  (Weekly Active Teams)  │
                    └───────────┬─────────────┘
                                │
            ┌───────────────────┼───────────────────┐
            ▼                   ▼                   ▼
    ┌───────────────┐   ┌───────────────┐   ┌───────────────┐
    │  Input: New   │   │ Input: Team   │   │  Input: Team  │
    │ Team Signups  │   │  Activation   │   │  Retention    │
    └───────┬───────┘   └───────┬───────┘   └───────┬───────┘
            │                   │                   │
    ┌───────┴───────┐   ┌───────┴───────┐   ┌───────┴───────┐
    │ • Traffic     │   │ • Onboarding  │   │ • Weekly      │
    │ • Signup rate │   │   completion  │   │   engagement  │
    │ • First team  │   │ • First value │   │ • Feature     │
    │   created     │   │   moment      │   │   depth       │
    └───────────────┘   └───────────────┘   └───────────────┘
```

### Good vs Bad Examples

**Good: Value-Focused**
```
Product: Project Management Tool
North Star: Weekly Active Projects with 3+ collaborators

Why good:
- Measures collaboration value (core purpose)
- "3+ collaborators" ensures real team usage
- Weekly timeframe balances signal and noise
- Teams can influence via activation, features, retention
```

**Bad: Vanity Metric**
```
Product: Project Management Tool
"North Star": Total Registered Users

Why bad:
- Doesn't measure ongoing value
- Includes churned users
- Doesn't differentiate engaged vs dormant
- Can't prioritize based on this
```

**Good: Leading Indicator**
```
Product: E-commerce Platform
North Star: Weekly purchasing customers

Why good:
- Measures actual value exchange
- Leading indicator of GMV
- Combines acquisition + retention
- Clear optimization paths
```

**Bad: Lagging Only**
```
Product: E-commerce Platform
"North Star": Annual Revenue

Why bad:
- Too slow to react to
- Teams can't see weekly impact
- Doesn't guide product decisions
- Finance metric, not product metric
```

### North Star for Different Stages

| Stage | North Star Focus | Example |
|-------|------------------|---------|
| **Pre-PMF** | Engagement intensity | Daily active rate of first 100 users |
| **Early Growth** | Activation + retention | Weekly users completing core action |
| **Scaling** | Sustainable growth | Monthly active + expansion revenue |
| **Mature** | Efficiency + expansion | Revenue per user, platform usage |

### Validating Your North Star

**Before committing, test these:**

1. **Correlation test**: Does improving this correlate with revenue growth historically?
2. **Prioritization test**: Would this help you decide between two features?
3. **Communication test**: Can you explain it to anyone in 30 seconds?
4. **Counter-metric test**: What could go wrong if you only optimize for this?

### Common North Star Mistakes

| Mistake | Problem | Better Alternative |
|---------|---------|-------------------|
| **Revenue** | Lagging, not product-focused | Weekly paying customers |
| **Total users** | Ignores churn, quality | Weekly/Monthly active users |
| **Sessions** | Activity ≠ value | Sessions with core action |
| **NPS** | Infrequent, hard to move | Usage-based proxy + NPS |
| **Multiple NSMs** | Defeats the purpose | Pick one, track others as KPIs |

### Anti-Patterns

- **Too many North Stars** — If everything is a priority, nothing is
- **Pure vanity** — "Total downloads" tells you nothing about value
- **Unchangeable** — If teams can't move it, it's not useful
- **Revenue-only** — Finance metric, not product metric
- **Ignoring quality** — "Messages sent" without "messages read"
- **Copying competitors** — Your NSM should reflect YOUR value prop
