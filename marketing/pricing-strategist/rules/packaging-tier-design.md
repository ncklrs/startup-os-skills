---
title: Tier Design and Packaging
impact: CRITICAL
tags: packaging, tiers, bundles, good-better-best, pricing
---

## Tier Design and Packaging

**Impact: CRITICAL**

How you package features into tiers determines which customers you attract, how much revenue you capture, and how customers perceive your value.

### The Good/Better/Best Framework

| Tier | Role | Target Customer | Pricing Strategy |
|------|------|-----------------|------------------|
| **Good (Starter)** | Entry point, low barrier | Price-sensitive, evaluators | Low anchor, limited margin |
| **Better (Pro)** | Main revenue driver | Core ICP, growth stage | Optimal margin, best value |
| **Best (Enterprise)** | Maximum value capture | High-value, complex needs | Value-based, custom |

### Tier Distribution Goals

```
Revenue Distribution (Healthy):
├── Starter (Good):     10-20% of customers, 5-10% of revenue
├── Pro (Better):       60-70% of customers, 40-50% of revenue
└── Enterprise (Best):  10-20% of customers, 40-50% of revenue

                                              ┌────────────┐
Revenue by Tier:                              │ Enterprise │
                          ┌────────────┐      │    45%     │
                          │    Pro     │      │            │
            ┌──────┐      │    40%     │      │            │
            │Start │      │            │      │            │
            │ 15%  │      │            │      │            │
            └──────┘      └────────────┘      └────────────┘
```

### Feature Allocation Matrix

| Feature Type | Starter | Pro | Enterprise |
|--------------|---------|-----|------------|
| **Core product** | Full | Full | Full |
| **Usage limits** | Low | Medium | High/Unlimited |
| **Collaboration** | Limited | Full team | Org-wide |
| **Integrations** | Basic | Popular | All + custom |
| **Security** | Standard | SSO | SSO + SCIM + audit |
| **Support** | Self-serve | Email/chat | Dedicated CSM |
| **SLA** | None | 99.9% | 99.99% + custom |
| **Data/Analytics** | Basic | Advanced | Custom + export |

### Feature Fencing Strategies

| Strategy | Description | Best For |
|----------|-------------|----------|
| **Usage-based** | Limit quantity, not capability | API calls, storage, seats |
| **Feature gates** | Reserve specific features | Advanced analytics, SSO |
| **Time gates** | Limit history/retention | Log retention, data history |
| **Speed gates** | Limit performance | Priority processing, SLAs |
| **Support gates** | Differentiate service | Response time, dedicated support |

### Good Tier Design Examples

```
✓ Clear value ladder:
├── Starter ($29): Solo developers
│   → 1 project, 1,000 API calls, community support
├── Pro ($99): Growing teams
│   → 10 projects, 50,000 API calls, email support
└── Enterprise (Custom): Large organizations
    → Unlimited, 24/7 support, SSO, dedicated CSM

✓ Feature progression makes sense:
├── Basic: Create and edit
├── Pro: + Collaborate and share
└── Enterprise: + Control and secure

✓ Each tier has a clear "hero" feature:
├── Starter: "Get started free"
├── Pro: "Team collaboration"
└── Enterprise: "Security & compliance"
```

### Bad Tier Design Examples

```
✗ Too many tiers:
├── Free
├── Starter ($9)
├── Basic ($19)
├── Pro ($39)
├── Team ($79)
├── Business ($149)
└── Enterprise (Custom)
  → Decision paralysis, unclear differentiation

✗ No logical feature progression:
├── Starter: 5 users, SSO, API access
├── Pro: 10 users, no SSO, no API
└── Enterprise: Unlimited, SSO, API
  → Why does Starter have features Pro doesn't?

✗ Starter is too limited:
├── Starter: 1 project, 100 API calls
  → Impossible to evaluate the product
```

### Bundle Psychology

| Bundle Type | Structure | Psychology |
|-------------|-----------|------------|
| **Pure bundling** | Only available together | Simplicity, forced value |
| **Mixed bundling** | Sold separately or together | Flexibility + bundle discount |
| **Add-on model** | Core + optional extras | Customization, expansion |
| **All-you-can-eat** | Everything included | Simplicity for buyer, risk for seller |

### Bundle Pricing Math

```
Unbundled:
├── Product A: $100
├── Product B: $80
└── Product C: $60
    Total if bought separately: $240

Bundled:
└── All three: $180 (25% discount)
    → Higher perceived value
    → Lower per-product price
    → Higher attachment rate
    → Harder for competitors to unbundle
```

### Naming Conventions

| Tier Level | Good Names | Avoid |
|------------|------------|-------|
| **Entry** | Starter, Basic, Essentials, Free | Lite, Trial, Cheap |
| **Middle** | Pro, Growth, Team, Plus | Standard, Normal |
| **Top** | Enterprise, Business, Scale, Premium | Ultimate, Diamond, VIP |

### Tier Naming Psychology

```
✓ Aspirational progression:
   Starter → Growth → Scale
   → Implies company trajectory

✓ Descriptive of use case:
   Personal → Team → Organization
   → Clear who each tier is for

✓ Value-oriented:
   Essentials → Professional → Enterprise
   → Implies increasing capabilities

✗ Confusing hierarchy:
   Basic → Standard → Premium → Ultimate → Enterprise
   → Too many levels, unclear differences
```

### Free Tier Strategy

| Strategy | Description | Best For |
|----------|-------------|----------|
| **Freemium** | Forever free with limits | PLG, high volume |
| **Free trial** | Time-limited full access | High-touch, consideration |
| **Reverse trial** | Start paid, downgrade option | SaaS, engagement |
| **Sandbox** | Limited/test environment | Developers, API products |

### Free Tier Limits

| Too Generous | Just Right | Too Restrictive |
|--------------|------------|-----------------|
| Full features forever | Core features, usage caps | Can't experience value |
| No incentive to upgrade | Clear upgrade triggers | Churns before converting |
| Supports freeloaders | Filters serious users | Filters good prospects too |

### Upgrade Triggers

| Trigger Type | Example | Placement |
|--------------|---------|-----------|
| **Usage limit hit** | "You've used 80% of your quota" | In-app notification |
| **Feature gate** | "SSO is available on Pro" | At feature access point |
| **Growth milestone** | "You have 5+ team members" | Dashboard, usage page |
| **Time trigger** | "Your trial ends in 3 days" | Email, modal |

### Plan Comparison Best Practices

| Element | Best Practice |
|---------|---------------|
| **Columns** | 3-4 tiers max (including free) |
| **Rows** | Highlight differences, not all features |
| **Checkmarks** | Partial vs full (limited, unlimited) |
| **Empty cells** | Show what's missing, not just what's included |
| **CTA** | Unique per tier (Start free, Try Pro, Contact sales) |
| **Highlight** | Mark recommended tier clearly |

### Anti-Patterns

- **Feature soup** — 50 features listed, customer can't process
- **False hierarchy** — Higher tiers don't have clear additional value
- **Missing middle** — Jump from $29 to $299 with nothing between
- **Punitive limits** — Starter so limited it's unusable
- **Complex add-ons** — Too many optional extras confuse pricing
- **Arbitrary gates** — Features in higher tiers that don't justify the price
- **No recommended tier** — Customer has to decide entirely on their own
- **Same price, different packaging** — Appears like arbitrary segmentation
