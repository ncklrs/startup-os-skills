---
title: Sales Tech Stack Integration
impact: HIGH
tags: integration, tech-stack, salesforce, hubspot, outreach, gong
---

## Sales Tech Stack Integration

**Impact: HIGH**

A well-integrated tech stack multiplies rep productivity. A poorly integrated one creates data silos, double entry, and frustration. Integration architecture is as important as tool selection.

### Sales Tech Stack Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                        ANALYTICS & BI LAYER                          │
│         Tableau • Looker • Power BI • Salesforce Reports            │
└────────────────────────────────┬────────────────────────────────────┘
                                 │
┌────────────────────────────────▼────────────────────────────────────┐
│                         CRM (Source of Truth)                        │
│                    Salesforce • HubSpot • Dynamics                   │
└───────┬─────────────────┬─────────────────┬─────────────────┬───────┘
        │                 │                 │                 │
┌───────▼───────┐ ┌───────▼───────┐ ┌───────▼───────┐ ┌───────▼───────┐
│  ENGAGEMENT   │ │ INTELLIGENCE  │ │   ENRICHMENT  │ │   COMMERCE    │
│               │ │               │ │               │ │               │
│ Outreach      │ │ Gong          │ │ ZoomInfo      │ │ Stripe        │
│ Salesloft     │ │ Chorus        │ │ Clearbit      │ │ Chargebee     │
│ Apollo        │ │ Clari         │ │ Apollo        │ │ CPQ           │
└───────────────┘ └───────────────┘ └───────────────┘ └───────────────┘
        │                 │                 │                 │
┌───────▼─────────────────▼─────────────────▼─────────────────▼───────┐
│                       INTEGRATION LAYER                              │
│              Workato • Zapier • Tray.io • Native APIs               │
└─────────────────────────────────────────────────────────────────────┘
```

### Tool Selection Criteria

| Criteria | Weight | Evaluation Questions |
|----------|--------|---------------------|
| **CRM Integration** | 30% | Native connector? Bi-directional sync? Real-time? |
| **Data Quality** | 20% | Does it improve or degrade CRM data? |
| **Rep Adoption** | 20% | Will reps actually use it? UX quality? |
| **Reporting** | 15% | Can we measure ROI? Data accessible? |
| **Security** | 10% | SOC 2? GDPR compliant? SSO support? |
| **Cost/Value** | 5% | ROI positive within 6 months? |

### Integration Patterns

**Pattern 1: CRM as Master (Recommended)**

```
ZoomInfo ──────► Salesforce ◄────── Outreach
                     │
                     ▼
              Single Source
               of Truth

Pros: Clear data ownership, no conflicts
Cons: CRM must be kept clean
```

**Pattern 2: Bi-Directional Sync**

```
Salesforce ◄────────► Outreach
    │                    │
    └──────► ◄──────────┘
       Sync conflicts possible

Pros: Data flows both ways
Cons: Risk of sync loops, data conflicts
```

**Pattern 3: Data Warehouse Hub**

```
Salesforce ────►┌─────────────┐
                │    Data     │────► Analytics
Outreach ──────►│  Warehouse  │
                │ (Snowflake) │────► ML Models
Gong ──────────►└─────────────┘

Pros: Decoupled, scalable analytics
Cons: Complexity, latency
```

### Common Integration Configurations

#### Salesforce + Outreach

```yaml
Integration: Salesforce ↔ Outreach
Type: Bi-directional
Sync Frequency: Real-time

Object Mappings:
  Lead → Prospect
  Contact → Prospect
  Account → Account
  Opportunity → Opportunity
  Task → Task (activities only)

Field Mappings:
  SFDC Lead.Status → Outreach Prospect.Stage
  Outreach Sequence.Status → SFDC Lead.Outreach_Status__c
  Outreach LastActivityDate → SFDC Contact.Last_Outreach_Activity__c

Sync Rules:
  - Outreach creates activities in SFDC (one-way)
  - SFDC owns account/contact data (master)
  - Sequence status syncs bi-directionally
  - Emails logged with full body
```

#### Salesforce + Gong

```yaml
Integration: Salesforce ↔ Gong
Type: Gong reads, SFDC writes
Sync Frequency: Near real-time (within minutes)

Data Flow:
  Gong → SFDC:
    - Call recordings linked to Contact/Opportunity
    - AI insights written to custom fields
    - Deal risk scores updated
    - Key moments flagged

  SFDC → Gong:
    - Account/Opportunity context
    - Deal stage for filtering
    - Owner for assignment

Custom Fields (SFDC):
  - Gong_Last_Call_Date__c
  - Gong_Deal_Risk_Score__c
  - Gong_Engagement_Score__c
  - Gong_Competitor_Mentioned__c
```

#### Salesforce + ZoomInfo

```yaml
Integration: ZoomInfo → Salesforce
Type: One-way enrichment
Sync Frequency: On-demand + daily batch

Enrichment Rules:
  Account:
    - Update if field is blank OR data is >90 days old
    - Fields: Industry, Employee Count, Revenue, Tech Stack
    - Never overwrite: Name, Owner, custom fields

  Contact:
    - Update if field is blank
    - Fields: Title, Phone, Email, LinkedIn URL
    - Create net-new contacts with approval workflow

Matching Logic:
  - Account: Domain match first, then Name + Location
  - Contact: Email match first, then Name + Company
```

### Integration Health Monitoring

```
┌────────────────────────────────────────────────────────────┐
│            INTEGRATION HEALTH DASHBOARD                     │
├────────────────────────────────────────────────────────────┤
│                                                             │
│ Integration          Status    Last Sync    Error Rate     │
│ ─────────────────────────────────────────────────────────  │
│ Salesforce↔Outreach  ✅ Active  2 min ago   0.1%          │
│ Salesforce↔Gong      ✅ Active  5 min ago   0.0%          │
│ Salesforce←ZoomInfo  ✅ Active  4 hrs ago   0.3%          │
│ Salesforce→Slack     ✅ Active  1 min ago   0.0%          │
│ Salesforce↔Stripe    ⚠️ Degraded 1 hr ago   2.1%          │
│                                                             │
│ Recent Errors:                                              │
│ • Stripe sync: 23 invoices failed mapping (field missing)  │
│ • ZoomInfo: Rate limit hit, resuming in 15 min            │
│                                                             │
│ Data Quality Impact:                                        │
│ • 150 contacts enriched today                              │
│ • 2,340 activities logged from Outreach                    │
│ • 89 calls recorded by Gong                                │
└────────────────────────────────────────────────────────────┘
```

### Integration Best Practices

| Practice | Description |
|----------|-------------|
| **Single source of truth** | Designate one system as master for each data type |
| **Field-level mapping docs** | Document every field that syncs between systems |
| **Error alerting** | Immediate notification on sync failures |
| **Audit trail** | Log all integration-created/modified records |
| **Sandbox testing** | Test all integrations in sandbox first |
| **Rollback plan** | Know how to undo integration changes |

### API Rate Limits & Quotas

| System | Daily Limit | Per-Minute | Workaround |
|--------|-------------|------------|------------|
| Salesforce | 1M/org | 600/user | Bulk API for large operations |
| HubSpot | 500K/day | 100/10sec | Batch API calls |
| Outreach | Varies by plan | 50/sec | Queuing system |
| ZoomInfo | Plan-based | 100/min | Scheduled batches |
| Gong | 1000/day | 10/sec | Webhook-based updates |

### Tech Stack ROI Measurement

```
Tool ROI Calculation:

Outreach:
├── Cost: $150/user/month × 20 users = $3,000/month
├── Time saved: 5 hrs/rep/week × 20 reps × $50/hr = $20,000/month
├── Additional meetings: +15% = ~$50,000 pipeline/month
└── ROI: ($70,000 - $3,000) / $3,000 = 2,233%

Gong:
├── Cost: $100/user/month × 30 users = $3,000/month
├── Win rate improvement: +3% = ~$30,000/month in revenue
├── Ramp time reduction: 2 weeks faster = $10,000 value
└── ROI: ($40,000 - $3,000) / $3,000 = 1,233%
```

### Migration Checklist

When adding/changing tools:

```markdown
## Pre-Migration
- [ ] Document current state (all integrations, field mappings)
- [ ] Identify data dependencies
- [ ] Test in sandbox environment
- [ ] Create rollback plan
- [ ] Schedule during low-activity period

## During Migration
- [ ] Pause affected integrations
- [ ] Run data validation pre/post
- [ ] Monitor error logs
- [ ] Verify critical workflows

## Post-Migration
- [ ] Enable monitoring/alerting
- [ ] Validate data quality
- [ ] Update documentation
- [ ] Train affected users
- [ ] Measure baseline metrics
```

### Anti-Patterns

- **Tool sprawl** — New tool for every problem
- **No integration strategy** — Tools operate in silos
- **CRM bypass** — Data entered in other tools, not CRM
- **Manual data sync** — "We export CSV and import weekly"
- **No error handling** — Silent integration failures
- **Undocumented integrations** — Only one person knows how it works
- **Over-syncing** — Every field syncs when few are needed
- **No sandbox testing** — Integration changes go straight to production
