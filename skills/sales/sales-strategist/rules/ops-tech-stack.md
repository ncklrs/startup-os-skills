---
title: Sales Tech Stack Selection
impact: MEDIUM-HIGH
tags: ops, technology, tools, CRM, enablement
---

## Sales Tech Stack Selection

**Impact: MEDIUM-HIGH**

Your tech stack should enable your process, not define it. Too many tools create context-switching hell. Too few leave reps doing manual work that should be automated. The best stacks are integrated, adopted, and measured.

### Tech Stack Layers

```
┌─────────────────────────────────────────────────────────────┐
│                    SALES TECH STACK                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  Layer 1: SYSTEM OF RECORD                           │  │
│  │  CRM (Salesforce, HubSpot, Pipedrive)               │  │
│  └──────────────────────────────────────────────────────┘  │
│                           │                                 │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  Layer 2: ENGAGEMENT                                 │  │
│  │  Sequencing, Dialers, Email                         │  │
│  │  (Outreach, Salesloft, Apollo)                      │  │
│  └──────────────────────────────────────────────────────┘  │
│                           │                                 │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  Layer 3: INTELLIGENCE                               │  │
│  │  Conversation, Forecasting, Signals                 │  │
│  │  (Gong, Chorus, Clari)                              │  │
│  └──────────────────────────────────────────────────────┘  │
│                           │                                 │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  Layer 4: DATA                                       │  │
│  │  Enrichment, Intent, Prospecting                    │  │
│  │  (ZoomInfo, Clearbit, 6sense)                       │  │
│  └──────────────────────────────────────────────────────┘  │
│                           │                                 │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  Layer 5: ENABLEMENT                                 │  │
│  │  Content, Training, CPQ                             │  │
│  │  (Highspot, Seismic, DealHub)                       │  │
│  └──────────────────────────────────────────────────────┘  │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Tool Selection by Category

**CRM (System of Record):**

| Tool | Best For | Price Range | Complexity |
|------|----------|-------------|------------|
| **Salesforce** | Enterprise, customization | $$$$$ | High |
| **HubSpot** | SMB/MM, marketing alignment | $-$$$$ | Medium |
| **Pipedrive** | SMB, simplicity | $-$$ | Low |
| **Close** | High-velocity sales | $$-$$$ | Low |
| **Attio** | Modern UI, customization | $$-$$$ | Medium |

**Sales Engagement:**

| Tool | Best For | Key Features | Integration |
|------|----------|--------------|-------------|
| **Outreach** | Enterprise, sequences | Workflows, AI | Salesforce native |
| **Salesloft** | Mid-market, coaching | Cadences, analytics | Broad |
| **Apollo** | SMB, data + outreach | Built-in data, sequences | HubSpot, SF |
| **Instantly** | Cold email scale | Unlimited accounts | API-based |
| **Reply.io** | Multi-channel | Email + LinkedIn | Good |

**Conversation Intelligence:**

| Tool | Best For | Key Features | Price |
|------|----------|--------------|-------|
| **Gong** | Enterprise, full-stack | Calls, deals, coaching | $$$$$ |
| **Chorus (ZoomInfo)** | Mid-market, ZoomInfo users | Integrated data | $$$$ |
| **Fireflies** | Budget-conscious | Transcription, search | $-$$ |
| **Fathom** | Free tier, individuals | Auto-summaries | Free-$$ |
| **Grain** | Clips and highlights | Sharing, CRM sync | $$-$$$ |

**Data and Enrichment:**

| Tool | Best For | Data Quality | Features |
|------|----------|--------------|----------|
| **ZoomInfo** | Enterprise, full-stack | High | Intent, engagement |
| **Apollo** | SMB, all-in-one | Good | Sequencing included |
| **Clearbit** | Tech companies | Very High | Enrichment focus |
| **Lusha** | Budget, phone numbers | Good | Simple |
| **Clay** | Customization | Aggregated | Waterfall enrichment |

### Stack by Company Stage

**Seed/Early ($0-$2M ARR):**
```
Essential Stack:
├── CRM: HubSpot Free or Pipedrive
├── Email: Gmail + basic tracking
├── Scheduling: Calendly
├── Data: Apollo (free tier) or LinkedIn Sales Nav
└── Notes: Notion or Google Docs

Total Cost: ~$100-300/month
Key principle: Keep it simple, avoid tech debt
```

**Growth ($2M-$10M ARR):**
```
Expanded Stack:
├── CRM: HubSpot Pro or Salesforce Essentials
├── Engagement: Apollo or Outreach (if SDR team)
├── Conversation: Gong or Chorus
├── Data: ZoomInfo or Apollo paid
├── Scheduling: Chili Piper (routing)
├── CPQ: PandaDoc or HubSpot Quotes
└── Analytics: CRM native + Gong

Total Cost: ~$2,000-5,000/month
Key principle: Foundation for scale
```

**Scale ($10M-$50M ARR):**
```
Full Stack:
├── CRM: Salesforce + CPQ
├── Engagement: Outreach or Salesloft
├── Conversation: Gong
├── Data: ZoomInfo + Clearbit
├── Intent: 6sense or Demandbase
├── Forecasting: Clari
├── Enablement: Highspot or Seismic
├── CPQ: DealHub or Salesforce CPQ
└── Analytics: InsightSquared or custom BI

Total Cost: ~$15,000-50,000/month
Key principle: Integration and automation
```

### Tool Evaluation Framework

**Before Adding Any Tool:**

```
TOOL EVALUATION CHECKLIST

Problem Definition:
□ What specific problem does this solve?
□ How are we solving it today?
□ What is the cost of not solving it?

Alternatives:
□ Can we solve this with existing tools?
□ What are the top 3 alternatives?
□ Have we demoed all of them?

Integration:
□ Does it integrate with our CRM?
□ Is the integration native or third-party?
□ What data flows between systems?

Adoption:
□ Who will use this daily?
□ What is the training requirement?
□ What happens if adoption is low?

Cost:
□ Total cost (licenses + implementation)?
□ Cost per user?
□ ROI calculation?

Security:
□ SOC 2 compliant?
□ Data handling/privacy?
□ Approved by IT/Security?
```

### Good Tech Stack Implementation

```
Stack Implementation Done Right:

Company: $8M ARR SaaS, 15 AEs

Stack:
├── CRM: HubSpot (clean, adopted)
├── Engagement: Apollo (sequences, data)
├── Conversation: Gong (coaching, forecasting)
├── Scheduling: Chili Piper (round robin)
└── Contracts: PandaDoc

Integration Map:
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  Apollo ──────► HubSpot ◄────── Gong                       │
│    │              │               │                         │
│    │              ▼               │                         │
│    └────────► Chili Piper ◄──────┘                         │
│                   │                                         │
│                   ▼                                         │
│               PandaDoc                                      │
│                                                             │
└─────────────────────────────────────────────────────────────┘

Why it works:
✓ Single source of truth (HubSpot)
✓ Bi-directional sync maintained
✓ Reps don't duplicate data entry
✓ Leadership gets accurate reports
✓ All tools have clear owners
```

### Bad Tech Stack Implementation

```
Stack Implementation Gone Wrong:

Company: $5M ARR SaaS, 10 AEs

Stack (accumulated over 3 years):
├── CRM: Salesforce (partially adopted)
├── Engagement: Outreach + Apollo + Reply.io
├── Conversation: Gong + Fireflies + Otter
├── Data: ZoomInfo + Lusha + RocketReach
├── Scheduling: Calendly + Chili Piper + HubSpot
├── Contracts: DocuSign + PandaDoc + HelloSign
└── More: 15 other tools "someone bought"

Problems:
✗ Multiple tools doing same thing
✗ No integration strategy
✗ Data in 3 places, none accurate
✗ Reps confused about which tool to use
✗ $40K/month in tool spend
✗ No one owns the stack

Reality:
- Salesforce 40% filled in
- Half the tools unused
- Reps use spreadsheets anyway
- Forecast from manual roll-up calls
```

### CRM Hygiene Requirements

**Minimum Required Fields:**

| Field | Why | Enforcement |
|-------|-----|-------------|
| Contact Email | Communication | Required on create |
| Company Name | Account mapping | Required on create |
| Deal Amount | Forecasting | Required on stage 2+ |
| Close Date | Forecasting | Required on all |
| Stage | Pipeline | Required, validated |
| Next Step | Activity | Required on stage 2+ |
| Source | Attribution | Required on create |

**Data Hygiene Rules:**

```
Automated Hygiene (CRM Workflows):

1. No activity 30+ days → Alert rep + manager
2. Close date passed → Force update or close
3. Deal in stage 60+ days → Review flag
4. Missing required fields → Can't progress stage
5. Duplicate contacts → Merge prompt
6. No next step → Can't leave deal view
```

### Tool Consolidation

**Signs You Need to Consolidate:**

- Same task can be done in 3+ tools
- Reps ask "where do I log this?"
- Data doesn't match across systems
- Tool spend >$500/rep/month
- Less than 60% adoption on any tool
- No one knows who owns which tool

**Consolidation Process:**

```
Step 1: Inventory
├── List all sales tools
├── Identify owner and users
├── Document actual usage (login data)
└── Calculate cost per tool

Step 2: Categorize
├── Essential (can't sell without)
├── Important (significant value)
├── Nice-to-have (limited use)
└── Unused (cancel immediately)

Step 3: Rationalize
├── One tool per category
├── Migrate data if needed
├── Provide transition time
└── Cancel redundant contracts

Step 4: Document
├── Official stack list
├── Owner for each tool
├── Governance process for new requests
└── Quarterly review schedule
```

### Anti-Patterns

- **Shiny object syndrome** — Buying every new tool
- **No integration plan** — Tools that don't talk
- **Tool as strategy** — "Gong will fix our coaching"
- **Rep as data entry** — Duplicate logging everywhere
- **No ownership** — Tools bought, never managed
- **Sunk cost fallacy** — Keeping tools because "we paid for it"
- **Over-tooling early** — Enterprise stack at seed stage
