---
title: CS Technology Stack Strategy
impact: HIGH
tags: technology, platform, tools, gainsight, churnzero, totango, integration
---

## CS Technology Stack Strategy

**Impact: HIGH**

Technology enables scale. Without the right tools, CSMs spend 40%+ of their time on data gathering and admin instead of customer engagement. But technology alone doesn't fix bad processes — it just automates them faster.

### The CS Tech Stack Layers

```
┌─────────────────────────────────────────────────────────────────┐
│                    INTELLIGENCE LAYER                            │
│  Churn prediction, next best action, AI insights                │
│  Planhat, Catalyst, Gainsight (PX), custom ML                   │
├─────────────────────────────────────────────────────────────────┤
│                    ENGAGEMENT LAYER                              │
│  In-app messaging, email automation, digital CS                 │
│  Intercom, Pendo, Appcues, Customer.io, Braze                   │
├─────────────────────────────────────────────────────────────────┤
│                    FEEDBACK LAYER                                │
│  NPS, CSAT, surveys, sentiment                                  │
│  Delighted, Wootric, Satismeter, Qualtrics                      │
├─────────────────────────────────────────────────────────────────┤
│                    ANALYTICS LAYER                               │
│  Product usage, feature adoption, behavioral data               │
│  Amplitude, Mixpanel, Pendo, Heap, Segment                      │
├─────────────────────────────────────────────────────────────────┤
│                    CS PLATFORM (CORE)                            │
│  Customer 360, health scores, playbooks, workflows              │
│  Gainsight, ChurnZero, Totango, Vitally, Planhat                │
├─────────────────────────────────────────────────────────────────┤
│                    CRM FOUNDATION                                │
│  Account data, contacts, opportunities, contracts               │
│  Salesforce, HubSpot, Dynamics                                  │
└─────────────────────────────────────────────────────────────────┘
```

### CS Platform Comparison

| Platform | Best For | Strengths | Considerations |
|----------|----------|-----------|----------------|
| **Gainsight** | Enterprise, complex | Most complete feature set | Complexity, cost |
| **ChurnZero** | Mid-market | In-app + CS platform | Less enterprise-grade |
| **Totango** | Modular needs | Flexibility, modules | Can become fragmented |
| **Vitally** | Startups, PLG | Modern UX, fast setup | Less mature |
| **Planhat** | European, modern | Clean design, revenue ops | Smaller ecosystem |
| **Catalyst** | Sales + CS alignment | CRM-integrated | Newer, evolving |

### Core CS Platform Capabilities

| Capability | Must Have | Nice to Have |
|------------|-----------|--------------|
| **Customer 360** | ● | |
| **Health scoring** | ● | |
| **Playbooks/workflows** | ● | |
| **Task management** | ● | |
| **Reporting/dashboards** | ● | |
| **Product usage integration** | ● | |
| **Email integration** | ● | |
| **CRM sync** | ● | |
| **NPS integration** | | ● |
| **In-app messaging** | | ● |
| **Churn prediction (AI)** | | ● |
| **Revenue forecasting** | | ● |
| **Digital programs** | | ● |

### Build vs Buy Decision

| Factor | Build | Buy |
|--------|-------|-----|
| **Time to value** | 6-12 months | 2-4 weeks |
| **Upfront cost** | Engineering time | License fees |
| **Ongoing cost** | Maintenance burden | Subscription |
| **Customization** | Unlimited | Platform constraints |
| **Best for** | Unique requirements | Standard CS operations |
| **Risk** | Opportunity cost, maintenance | Vendor dependency |

**Build when:**
```
□ You have truly unique requirements
□ You have engineering capacity
□ Time to value isn't critical
□ Data security requires on-premise
□ You want full control
```

**Buy when:**
```
□ You need standard CS capabilities
□ You need fast time to value
□ You don't have engineering capacity
□ You want vendor to handle innovation
□ You want proven best practices
```

### Data Integration Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                     DATA SOURCES                                 │
├──────────────┬──────────────┬──────────────┬───────────────────┤
│ CRM          │ Product      │ Support      │ Billing           │
│ (Salesforce) │ (Amplitude)  │ (Zendesk)    │ (Stripe)          │
└──────┬───────┴──────┬───────┴──────┬───────┴───────┬───────────┘
       │              │              │               │
       ▼              ▼              ▼               ▼
┌─────────────────────────────────────────────────────────────────┐
│                   DATA WAREHOUSE / CDP                           │
│              (Snowflake, BigQuery, Segment)                      │
└───────────────────────────┬─────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────────┐
│                     CS PLATFORM                                  │
│                   (Gainsight, etc.)                              │
│  ┌───────────┐ ┌───────────┐ ┌───────────┐ ┌───────────┐       │
│  │ Customer  │ │ Health    │ │ Playbooks │ │ Reporting │       │
│  │ 360       │ │ Scores    │ │           │ │           │       │
│  └───────────┘ └───────────┘ └───────────┘ └───────────┘       │
└─────────────────────────────────────────────────────────────────┘
```

### Key Integrations

| Integration | Purpose | Priority |
|-------------|---------|----------|
| **CRM → CS Platform** | Account, contact, opportunity data | Critical |
| **Product → CS Platform** | Usage, adoption, feature data | Critical |
| **Support → CS Platform** | Tickets, sentiment, CSAT | High |
| **Billing → CS Platform** | MRR, contract, payment status | High |
| **CS Platform → CRM** | Health scores, CSM activities | High |
| **NPS Tool → CS Platform** | Survey responses, scores | Medium |
| **Calendar → CS Platform** | Meeting tracking, activities | Medium |
| **Email → CS Platform** | Email tracking, engagement | Medium |

### Good Technology Strategy

```
✓ Start with process, then automate
  → Define playbooks before implementing
  → Technology accelerates, doesn't create

✓ Single source of truth
  → CS platform is the system of record for health
  → CRM is system of record for account data
  → Clear ownership

✓ Data quality first
  → Garbage in, garbage out
  → Clean data before implementing health scores

✓ Phased implementation
  → Core first (360, health, playbooks)
  → Add layers (automation, AI) over time

✓ Adoption > Features
  → 80% adoption of 20% features
  → Better than 20% adoption of 80% features

✓ Integrate, don't duplicate
  → Don't rebuild what exists in other tools
  → Connect systems, don't recreate
```

### Bad Technology Strategy

```
✗ Tool before process
  → "We bought Gainsight, now what?"
  → Technology won't fix bad processes

✗ Too many tools
  → 15 tools, no integration
  → CSMs live in spreadsheets anyway

✗ No data governance
  → Multiple sources of truth
  → Conflicting numbers in meetings

✗ Shelfware
  → Expensive platform, minimal usage
  → Overpaid for features not used

✗ Custom everything
  → Every field, every workflow custom
  → Nightmare to maintain

✗ No owner
  → Who maintains the CS platform?
  → Becomes stale without steward
```

### Implementation Checklist

```
PHASE 1: Foundation (Weeks 1-4)
□ CRM integration configured
□ Account hierarchy established
□ Contact sync working
□ Basic customer 360 live
□ CSM assignments configured

PHASE 2: Health Scoring (Weeks 5-8)
□ Product usage integration
□ Health score components defined
□ Health score weights calibrated
□ Health score dashboards created
□ Alert rules configured

PHASE 3: Playbooks (Weeks 9-12)
□ Onboarding playbook implemented
□ At-risk playbook implemented
□ QBR playbook implemented
□ Renewal playbook implemented
□ Task automation configured

PHASE 4: Optimization (Weeks 13-16)
□ Reporting suite finalized
□ Email integration complete
□ Team fully trained
□ Process compliance tracking
□ Health score validation complete
```

### CS Platform Adoption Metrics

| Metric | Target | Why |
|--------|--------|-----|
| **Daily active CSMs** | 90%+ | Platform is useful |
| **Tasks completed in platform** | 80%+ | Not using spreadsheets |
| **Playbook compliance** | 85%+ | Processes followed |
| **Data freshness** | <24 hours | Integrations working |
| **Health score coverage** | 95%+ | All accounts scored |

### Technology Budget Allocation

| Category | % of CS Tech Budget |
|----------|---------------------|
| **CS Platform** | 40-50% |
| **Analytics tools** | 15-20% |
| **Engagement tools** | 15-20% |
| **Integration/data** | 10-15% |
| **Feedback tools** | 5-10% |

### Common Platform Mistakes

| Mistake | Symptom | Fix |
|---------|---------|-----|
| No CS Ops owner | Platform stale, low adoption | Dedicated CS Ops role |
| Over-customization | Fragile, hard to update | Stick to OOTB when possible |
| No training | CSMs don't use it | Formal enablement program |
| Data quality issues | Health scores meaningless | Data governance process |
| Too many automations | Customers over-messaged | Audit and consolidate |
| Siloed from CRM | Duplicate data entry | Proper bi-directional sync |

### Vendor Evaluation Criteria

| Criteria | Weight | Assessment Method |
|----------|--------|-------------------|
| **Fit for segment** | 25% | Demo, references |
| **Integration capability** | 20% | Technical review |
| **Ease of use** | 15% | Trial, user feedback |
| **Total cost of ownership** | 15% | Full cost analysis |
| **Implementation support** | 10% | References, SOW review |
| **Roadmap alignment** | 10% | Product briefing |
| **Vendor stability** | 5% | Financial review |

### Anti-Patterns

- **Tool without process** — Technology amplifies, doesn't create
- **Data hoarding** — Every metric tracked, none acted upon
- **Integration debt** — Manual CSV uploads, stale data
- **Feature bloat** — Buying features CSMs will never use
- **No steward** — Platform becomes abandoned shelfware
- **Siloed tools** — Every team has their own tool, no integration
- **Over-automation** — Customers get 15 automated emails per week
- **Analysis paralysis** — Evaluating tools for 6 months instead of implementing
