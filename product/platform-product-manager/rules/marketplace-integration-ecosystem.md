---
title: Integration Marketplace Strategy
impact: MEDIUM
tags: marketplace, integrations, partners, ecosystem
---

## Integration Marketplace Strategy

**Impact: MEDIUM**

An integration marketplace multiplies your platform's value. Every integration makes your platform stickier and more valuable.

### Marketplace Maturity Stages

| Stage | Integrations | Focus | Strategy |
|-------|--------------|-------|----------|
| **Bootstrap** | 0-10 | Core integrations | Build in-house |
| **Foundation** | 10-50 | Key categories | Partner outreach |
| **Growth** | 50-200 | Long tail | Self-serve partner portal |
| **Scale** | 200+ | Ecosystem flywheel | Revenue sharing, acquisition |

### Integration Types

| Type | Who Builds | Maintenance | Example |
|------|-----------|-------------|---------|
| **Native** | Your team | You | Core CRM sync |
| **Partner-built** | Partners | Partner | Salesforce connector |
| **Community** | Developers | Community | Open source tools |
| **Embedded** | Your platform | You | White-label options |

### Integration Prioritization Framework

**Score each integration (1-5):**

| Factor | Weight | Questions |
|--------|--------|-----------|
| **Customer demand** | 30% | How many customers request this? |
| **Retention impact** | 25% | Will this reduce churn? |
| **Acquisition impact** | 20% | Will this drive new signups? |
| **Strategic fit** | 15% | Does this support our positioning? |
| **Build effort** | 10% | How hard is this to build? |

**Integration Priority Matrix:**

```
                    HIGH DEMAND
                         │
           ┌─────────────┼─────────────┐
           │  PARTNER    │   BUILD     │
           │  FIRST      │   NOW       │
           │             │             │
LOW EFFORT─┼─────────────┼─────────────┼─HIGH EFFORT
           │             │             │
           │  DEPRIORITIZE  PARTNER    │
           │             │   ONLY      │
           └─────────────┼─────────────┘
                         │
                    LOW DEMAND
```

### Partner Portal Requirements

**Self-serve partner program needs:**

| Feature | Priority | Purpose |
|---------|----------|---------|
| **Registration** | Critical | Onboard partners |
| **API documentation** | Critical | Build integrations |
| **Sandbox environment** | Critical | Test without risk |
| **App submission** | Critical | List integrations |
| **Review dashboard** | High | Track status |
| **Analytics** | High | Usage metrics |
| **Revenue reports** | Medium | Payouts, tracking |
| **Co-marketing tools** | Medium | Launch support |

### Integration Listing Page Anatomy

**Good marketplace listing:**

```markdown
# Slack Integration

Connect your Example account to Slack for real-time notifications.

## Features
- Get notified when orders are placed
- Receive alerts for failed payments
- Daily summary reports to channel

## Setup (2 minutes)
1. Click "Connect Slack"
2. Choose your workspace
3. Select notification channel
4. Configure alert preferences

## Pricing
Free with all plans

## Requirements
- Slack workspace admin access
- Example account (any plan)

[Install Integration]

---

## Reviews (4.8 ★ from 234 reviews)

"This saves our team hours every week..." - Sarah, Acme Corp

## Support
Built by Example • support@example.com
```

### Revenue Sharing Models

| Model | Structure | Best For |
|-------|-----------|----------|
| **Free listing** | No fees | Early marketplace |
| **Revenue share** | 15-30% of integration revenue | Mature marketplace |
| **Flat fee** | $X/month listing | High-value integrations |
| **Tiered** | Better terms at scale | Growing partners |
| **Referral bonus** | % of referred revenue | Acquisition-focused |

**Example revenue share tiers:**

| Partner Revenue | Your Take Rate |
|-----------------|----------------|
| $0 - $10K/mo | 30% |
| $10K - $50K/mo | 25% |
| $50K - $100K/mo | 20% |
| $100K+/mo | 15% |

### Integration Quality Standards

**Certification requirements:**

| Requirement | Reason |
|-------------|--------|
| **Working demo** | Proves functionality |
| **Error handling** | Reliable user experience |
| **Documentation** | User can self-serve |
| **Support contact** | Issues can be resolved |
| **Security review** | Protect user data |
| **Performance test** | Won't degrade platform |
| **OAuth compliance** | Proper authentication |

### Partner Success Metrics

| Metric | Definition | Target |
|--------|------------|--------|
| **Install rate** | Installs / Listing views | > 10% |
| **Activation rate** | Active / Installed | > 50% |
| **Retention** | Still active at 90 days | > 70% |
| **NPS** | Partner satisfaction | > 40 |
| **Support ratio** | Tickets / Active installs | < 5% |

### Go-to-Market for Integrations

**Launch checklist:**

```
□ Integration working in production
□ Listing page complete
□ Documentation published
□ Support team briefed
□ Blog post drafted
□ Email to existing users
□ Social media posts scheduled
□ Partner co-marketing aligned
□ Sales team enablement
□ Success metrics defined
```

### Marketplace Categories

**Organize integrations by:**

| Category Type | Examples |
|---------------|----------|
| **Use case** | Marketing, Sales, Support |
| **Tool type** | CRM, Analytics, Communication |
| **Industry** | Healthcare, Finance, Retail |
| **Functionality** | Import, Export, Sync, Automate |

### Webhook Marketplace Pattern

**For event-based integrations:**

```
Your Platform → Webhook Events → Partner Apps

Events available:
- order.created
- order.updated
- customer.created
- payment.completed
- subscription.cancelled

Partner registers endpoint:
POST https://partner.com/webhook
Headers: X-Signature: sha256=...
Body: { event, data, timestamp }
```

### Build vs Partner vs Buy

| Factor | Build | Partner | Buy/Acquire |
|--------|-------|---------|-------------|
| **Control** | Full | Limited | Full |
| **Speed** | Slow | Medium | Fast |
| **Cost** | High | Low | Very High |
| **Quality** | High | Variable | High |
| **Maintenance** | You | Partner | You |

**Decision framework:**
- **Build** when: Core to value prop, strategic, high quality bar
- **Partner** when: Not core, partner has expertise, speed matters
- **Buy** when: Critical gap, strong partner exists, can afford

### Anti-Patterns

- **Vanity integrations** — Building for logos, not users
- **No quality bar** — Approving broken integrations
- **Zombie marketplace** — Integrations nobody uses
- **Partner neglect** — No support for integration builders
- **Revenue obsession** — High take rates killing ecosystem
- **Certification theater** — Badges without real review
- **Category sprawl** — Too many categories, hard to navigate
- **No removal process** — Can't sunset bad integrations
- **Competitive blindness** — Not integrating with competitors
