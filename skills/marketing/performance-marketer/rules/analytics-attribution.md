---
title: Attribution Modeling
impact: HIGH
tags: attribution, analytics, tracking, measurement
---

## Attribution Modeling

**Impact: HIGH**

Attribution determines which channels get credit for conversions. Wrong attribution leads to wrong decisions and wasted budget.

### Attribution Models Overview

| Model | How It Works | Best For |
|-------|--------------|----------|
| **Last Click** | 100% credit to final touchpoint | Direct response, simple funnels |
| **First Click** | 100% credit to first touchpoint | Understanding awareness |
| **Linear** | Equal credit across all touchpoints | Multi-channel, long cycles |
| **Time Decay** | More credit to recent touchpoints | Consideration stage analysis |
| **Position-Based** | 40% first, 40% last, 20% middle | Balanced view |
| **Data-Driven** | ML-based, platform-specific | High volume, sophisticated |

### Model Comparison Example

Customer journey: Google Ad → Blog Post → LinkedIn → Demo → Close

| Model | Google | Blog | LinkedIn | Demo |
|-------|--------|------|----------|------|
| Last Click | 0% | 0% | 0% | 100% |
| First Click | 100% | 0% | 0% | 0% |
| Linear | 25% | 25% | 25% | 25% |
| Time Decay | 10% | 15% | 25% | 50% |
| Position-Based | 40% | 10% | 10% | 40% |

### When to Use Each Model

| Situation | Recommended Model | Why |
|-----------|------------------|-----|
| Short sales cycle (<7 days) | Last Click | Few touchpoints |
| Long sales cycle (30+ days) | Linear or Position-Based | Many touchpoints matter |
| Brand building focus | First Click | See what drives awareness |
| Retargeting heavy | Time Decay | Recent > distant |
| High volume, good data | Data-Driven | Let ML optimize |
| Just getting started | Position-Based | Balanced, forgiving |

### Multi-Touch Attribution Setup

```
1. Define conversion events
   └── Primary: Trial signup, demo request, purchase
   └── Secondary: Pricing page, feature page, content DL

2. Identify touchpoints
   └── Paid: Google, Meta, LinkedIn
   └── Organic: SEO, direct, referral
   └── Owned: Email, blog, social

3. Connect data sources
   └── Ad platforms → Analytics → CRM

4. Set lookback window
   └── B2C: 7-30 days
   └── B2B: 30-90 days

5. Choose model
   └── Start with position-based
   └── Move to data-driven when mature
```

### Tracking Implementation

| Layer | Tools | Purpose |
|-------|-------|---------|
| **Web Analytics** | GA4, Mixpanel, Amplitude | User journey |
| **Ad Tracking** | Platform pixels, CAPI | Channel performance |
| **CRM** | HubSpot, Salesforce | Lead → Customer |
| **Data Warehouse** | BigQuery, Snowflake | Unified view |
| **Attribution Tool** | Segment, Triple Whale | Cross-channel model |

### UTM Parameter Standards

```
utm_source    = where traffic comes from (google, linkedin, email)
utm_medium    = marketing medium (cpc, social, email)
utm_campaign  = campaign name (spring-sale, product-launch)
utm_content   = creative variation (blue-button, video-a)
utm_term      = keyword (for paid search)
```

### UTM Best Practices

```
✓ Good UTM structure:
?utm_source=linkedin
&utm_medium=cpc
&utm_campaign=2024-q1-awareness
&utm_content=carousel-testimonials

✗ Bad UTM structure:
?utm_source=LinkedIn%20Ad%20Campaign%20March
(spaces, inconsistent naming, no other parameters)
```

### UTM Naming Convention

| Parameter | Convention | Example |
|-----------|------------|---------|
| Source | Lowercase, platform name | google, meta, linkedin |
| Medium | Lowercase, channel type | cpc, email, organic |
| Campaign | date-objective-audience | 2024q1-awareness-smb |
| Content | creative-variant | carousel-v2, video-demo |
| Term | keyword or targeting | secrets-management |

### Attribution Challenges

| Challenge | Solution |
|-----------|----------|
| **Cross-device** | Login-based tracking, probabilistic matching |
| **iOS privacy** | Server-side tracking, Conversions API |
| **Ad blockers** | First-party data, server-side pixels |
| **Long sales cycles** | Extended lookback windows |
| **Offline conversions** | CRM integration, import API |
| **View-through** | Platform-specific, usually overcounts |

### Good Attribution Practices

```
✓ Compare multiple models
  → Last-click says cut SEO, position-based shows it drives awareness

✓ Segment by customer type
  → Enterprise has different journey than SMB

✓ Regular attribution audits
  → Check tracking is working, parameters are consistent

✓ Use control groups
  → Measure incrementality, not just attribution
```

### Bad Attribution Practices

```
✗ Trusting only last-click
  → Overvalues bottom-funnel, undervalues awareness

✗ Platform-reported conversions only
  → Each platform takes credit, totals exceed actual conversions

✗ Ignoring assisted conversions
  → First/middle touches build the pipeline

✗ No offline conversion tracking
  → B2B especially needs CRM integration

✗ Set-and-forget tracking
  → UTM parameters drift, pixels break
```

### View-Through vs Click-Through

| Type | What It Measures | Reliability |
|------|------------------|-------------|
| **Click-Through** | User clicked ad, then converted | High |
| **View-Through** | User saw ad, converted later | Low-Medium |

**View-through guidance:**
- Useful for awareness/brand campaigns
- Default windows often too long (reduce to 1-7 days)
- Easy to over-count (same user sees many ads)
- Better for display/video than search

### Incrementality Testing

Attribution shows correlation. Incrementality shows causation.

| Method | How It Works | Accuracy |
|--------|--------------|----------|
| **Holdout tests** | Geographic or audience holdouts | High |
| **Lift studies** | Platform-provided (Meta, Google) | Medium-High |
| **On/Off tests** | Pause channel, measure impact | Medium |
| **Matched markets** | Compare similar regions | Medium |

### Anti-Patterns

- **Last-click worship** — Ignores awareness and consideration
- **Trusting platform numbers** — Each platform overclaims
- **No lookback window management** — Default windows are too long
- **Ignoring dark social** — Not all traffic is trackable
- **View-through over-reliance** — Easy to inflate
- **No holdout testing** — Attribution ≠ causation
- **Inconsistent UTMs** — Garbage in, garbage out
