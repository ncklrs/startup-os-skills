---
title: Customer Data Enrichment & 360 View
impact: HIGH
tags: data-enrichment, customer-360, data-quality, data-integration
---

## Customer Data Enrichment & 360 View

**Impact: HIGH**

A complete customer view is the foundation of effective health scoring and risk prediction. Data enrichment fills gaps, adds context, and creates a unified picture that enables proactive customer success. Without comprehensive data, even the best health models fail.

### The Customer 360 Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                      CUSTOMER 360 VIEW                           │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐              │
│  │   COMPANY   │  │  CONTACTS   │  │  CONTRACT   │              │
│  │   PROFILE   │  │  & ROLES    │  │   DETAILS   │              │
│  └─────────────┘  └─────────────┘  └─────────────┘              │
│                                                                  │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐              │
│  │   PRODUCT   │  │   SUPPORT   │  │   BILLING   │              │
│  │   USAGE     │  │   HISTORY   │  │   HISTORY   │              │
│  └─────────────┘  └─────────────┘  └─────────────┘              │
│                                                                  │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐              │
│  │   COMMS     │  │   SUCCESS   │  │  EXTERNAL   │              │
│  │   HISTORY   │  │   METRICS   │  │   SIGNALS   │              │
│  └─────────────┘  └─────────────┘  └─────────────┘              │
│                                                                  │
│                    ┌─────────────────┐                          │
│                    │   HEALTH SCORE  │                          │
│                    │   & RISK MODEL  │                          │
│                    └─────────────────┘                          │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘
```

### Data Source Categories

| Category | Data Types | Sources | Refresh Frequency |
|----------|------------|---------|-------------------|
| **Firmographics** | Company size, industry, location | Clearbit, ZoomInfo, LinkedIn | Monthly |
| **Technographics** | Tech stack, integrations used | BuiltWith, G2, product data | Monthly |
| **Intent Signals** | Research activity, content engagement | Bombora, 6sense, website | Weekly |
| **Financial** | Funding, revenue, growth | Crunchbase, PitchBook | Monthly |
| **Social** | News, sentiment, job postings | LinkedIn, news APIs | Daily |
| **Contact** | Email, phone, role, hierarchy | CRM, LinkedIn, email tools | Weekly |
| **Behavioral** | Product usage, engagement | Product analytics | Real-time |
| **Feedback** | NPS, CSAT, surveys | Survey tools | Event-driven |

### Good Data Enrichment Strategy

```
Customer Profile: Acme Corp

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

COMPANY INFORMATION (Enriched)
├── Legal Name: Acme Corporation
├── Industry: SaaS / B2B Technology
├── Employee Count: 450 (↑ 15% YoY)
├── Annual Revenue: $45M (estimated)
├── Funding: Series C, $28M raised
├── HQ Location: San Francisco, CA
├── Founded: 2018
└── Growth Stage: Scale-up

TECHNOGRAPHICS
├── CRM: Salesforce
├── Marketing: HubSpot
├── Support: Zendesk
├── Analytics: Mixpanel
├── Integrations Active: Salesforce, Slack
└── Potential Integrations: HubSpot, Zendesk

CONTACT INTELLIGENCE
├── Decision Makers: 3 identified
├── Champion: Sarah Chen (Head of Ops)
├── Executive Sponsor: Michael Torres (VP)
├── Billing Contact: Finance team
├── Power Users: 8 identified
└── Stakeholder Health: Strong

INTENT SIGNALS
├── Competitor Research: None detected
├── Content Engagement: 12 articles last month
├── Webinar Attendance: Attended 2 of 3 offered
└── Community Activity: Active in user group

EXTERNAL SIGNALS
├── Recent News: Announced new product line
├── Job Postings: Hiring 3 ops roles (expansion signal)
├── LinkedIn Activity: Champion posted about our product
└── Sentiment: Positive social mentions

DERIVED INSIGHTS
├── Expansion Potential: High (hiring, growing)
├── Churn Risk Factors: None detected
├── Recommended Actions: Upsell conversation
└── Next Best Action: Schedule expansion QBR
```

### Bad Data Enrichment Strategy

```
Customer Profile: Acme Corp

Company Name: Acme Corp
Contact: Sarah
Email: sarah@acme.com
Plan: Enterprise
MRR: $10,000

Problems:
✗ Minimal company context
✗ No firmographic enrichment
✗ No contact role or hierarchy
✗ No intent or external signals
✗ No usage data integration
✗ No derived insights
✗ No next best action
✗ Static, not dynamic data
```

### Key Enrichment Fields

| Field | Source | Use in Health Scoring |
|-------|--------|----------------------|
| **Employee count** | Clearbit, ZoomInfo | Growth signal, seat potential |
| **Industry** | Clearbit | Segment benchmarking |
| **Funding stage** | Crunchbase | Expansion potential |
| **Tech stack** | BuiltWith | Integration opportunities |
| **Job postings** | LinkedIn | Growth/contraction signals |
| **News mentions** | News APIs | Organizational changes |
| **Social sentiment** | LinkedIn, Twitter | Brand health |
| **Contact changes** | LinkedIn | Champion risk |
| **Competitor research** | Intent data | Competitive threat |

### Contact Enrichment Strategy

```
Contact Hierarchy Mapping:

Executive Level
├── CEO: John Smith
│   └── Relationship: Met once, annual review
├── CFO: Lisa Wong
│   └── Relationship: Billing escalations only
└── VP Operations: Michael Torres (Exec Sponsor)
    └── Relationship: Monthly check-ins ✓

Management Level
├── Head of Ops: Sarah Chen (Champion)
│   └── Relationship: Weekly calls ✓
├── IT Director: David Park
│   └── Relationship: Technical contact
└── Finance Manager: Amy Liu
    └── Relationship: Billing contact

User Level
├── Power Users: 8 identified
├── Regular Users: 23 active
└── Dormant Users: 4 inactive

Stakeholder Health Score: 78/100
├── Champion strength: Strong
├── Multi-threading: Good (4 relationships)
├── Executive access: Moderate
└── Risk: Champion single point of failure
```

### Data Quality Framework

| Dimension | Definition | Target | Measurement |
|-----------|------------|--------|-------------|
| **Completeness** | % of fields populated | >85% | Filled fields / Total fields |
| **Accuracy** | % of correct data | >90% | Validated / Total records |
| **Freshness** | Age of data | <30 days | Days since last update |
| **Consistency** | Data matches across systems | >95% | Matching / Total |
| **Uniqueness** | No duplicate records | >99% | Unique / Total records |

### Data Quality Dashboard

```
Customer Data Quality Report

┌─────────────────────────────────────────────────────────────────┐
│  OVERALL DATA QUALITY SCORE: 81%                                │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Completeness by Category:                                      │
│  ├── Company Profile:     ████████████████████ 92%             │
│  ├── Contact Data:        █████████████████░░░ 78%             │
│  ├── Product Usage:       ████████████████████ 96%             │
│  ├── Support History:     █████████████████░░░ 82%             │
│  ├── External Signals:    ████████████░░░░░░░░ 58%             │
│  └── Financial Data:      ██████████████████░░ 89%             │
│                                                                 │
│  Data Freshness:                                                │
│  ├── Updated <7 days:     65% of accounts                      │
│  ├── Updated 8-30 days:   28% of accounts                      │
│  └── Updated >30 days:    7% of accounts (⚠ stale)            │
│                                                                 │
│  Data Issues:                                                   │
│  ├── Missing champion:    23 accounts                          │
│  ├── Invalid email:       12 contacts                          │
│  ├── Duplicate contacts:  8 records                            │
│  └── Stale firmographics: 34 accounts                          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Integration Architecture

| System | Data Flow | Frequency | Key Fields |
|--------|-----------|-----------|------------|
| **CRM (Salesforce)** | Bi-directional | Real-time | Contacts, opportunities, notes |
| **Product** | Inbound | Hourly | Usage events, feature adoption |
| **Support (Zendesk)** | Inbound | Real-time | Tickets, sentiment, resolution |
| **Billing (Stripe)** | Inbound | Real-time | Payments, invoices, MRR |
| **Enrichment (Clearbit)** | Inbound | Daily | Firmographics, contacts |
| **Intent (Bombora)** | Inbound | Weekly | Research signals, topics |
| **Health Score** | Outbound | Daily | Score, risk tier, signals |

### Data Governance Principles

```
1. Single Source of Truth
   - Define master system for each data type
   - Health score is calculated, not stored in CRM
   - CRM is master for relationships
   - Product database is master for usage

2. Ownership
   - Each data field has a defined owner
   - Owner responsible for quality
   - Regular audits by data team

3. Access Control
   - Sensitive data (PII) protected
   - Role-based access
   - Audit logging enabled

4. Privacy Compliance
   - GDPR / CCPA compliant enrichment
   - Consent management
   - Data retention policies
   - Right to deletion supported
```

### Enrichment ROI Calculation

| Metric | Before Enrichment | After Enrichment | Improvement |
|--------|-------------------|------------------|-------------|
| Health score accuracy | 62% | 78% | +16% |
| Churn prediction lead time | 45 days | 72 days | +27 days |
| CSM research time | 25 min/account | 8 min/account | -68% |
| Expansion identification | 35% | 58% | +23% |
| False positive rate | 32% | 18% | -14% |

### Data Enrichment Checklist

```
□ Core Customer Data
  □ Company name and legal entity
  □ Industry and sub-industry
  □ Employee count and trend
  □ Location (HQ and offices)
  □ Website and social profiles

□ Contact Data
  □ Key contacts identified
  □ Roles and hierarchy mapped
  □ Email and phone validated
  □ LinkedIn profiles linked
  □ Champion and sponsor flagged

□ Financial Data
  □ Contract details accurate
  □ MRR/ARR calculated correctly
  □ Payment history current
  □ Renewal dates tracked
  □ Expansion history captured

□ Behavioral Data
  □ Product usage integrated
  □ Support tickets linked
  □ Communication history captured
  □ Engagement metrics calculated
  □ Feature adoption tracked

□ External Signals
  □ Firmographic enrichment active
  □ Intent data flowing
  □ News monitoring enabled
  □ Job posting tracking
  □ Social sentiment captured

□ Data Quality
  □ Completeness monitored
  □ Freshness tracked
  □ Duplicates resolved
  □ Validation rules in place
  □ Regular audits scheduled
```

### Anti-Patterns

- **Data silos** — Product data separate from CRM separate from support
- **Manual enrichment** — Relying on CSMs to research and update
- **Stale data** — Firmographics from years ago
- **Over-collection** — Gathering data without clear use case
- **No single source of truth** — Conflicting data across systems
- **Privacy violations** — Enriching without consent
- **Ignoring data quality** — Garbage in, garbage out
- **Under-utilization** — Rich data not surfaced to users
