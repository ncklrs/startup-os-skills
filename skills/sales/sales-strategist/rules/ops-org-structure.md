---
title: Sales Organization Structure and Roles
impact: HIGH
tags: ops, organization, roles, structure, hiring
---

## Sales Organization Structure and Roles

**Impact: HIGH**

Your org structure determines how information flows, how deals get worked, and how reps develop. The wrong structure creates friction, dropped balls, and turf wars. The right structure enables focus, specialization, and scale.

### Sales Org Evolution

**Stage-Based Structure:**

| Stage | ARR | Structure | Key Roles |
|-------|-----|-----------|-----------|
| **Seed** | $0-$500K | Founder sells | Founder as AE |
| **Early** | $500K-$2M | First AE(s) | 1-3 AEs, founder backup |
| **Growth** | $2M-$10M | Specialized roles | SDRs, AEs, CSM, Manager |
| **Scale** | $10M-$50M | Segments + Specialists | Teams by segment, SEs, Ops |
| **Enterprise** | $50M+ | Full org | VPs, Directors, full stack |

### Role Definitions

**SDR/BDR (Sales/Business Development Rep):**
```
Focus: Pipeline generation
Metrics: Meetings booked, qualified opportunities
Reports to: SDR Manager or Sales Manager

Responsibilities:
├── Outbound prospecting (calls, emails, social)
├── Inbound lead qualification
├── Meeting scheduling for AEs
├── CRM data hygiene
└── Handoff documentation

NOT Responsible For:
├── Closing deals
├── Pricing discussions
├── Contract negotiation
└── Long-term account management

Career Path: SDR → Sr. SDR → AE or SDR Manager
Typical Tenure in Role: 12-24 months
```

**AE (Account Executive):**
```
Focus: Closing new business
Metrics: Bookings, revenue, win rate
Reports to: Sales Manager or Director

Responsibilities:
├── Discovery and qualification
├── Demos and presentations
├── Proposal creation
├── Negotiation and closing
├── Forecasting
└── Pipeline management

NOT Responsible For (unless hybrid):
├── Cold prospecting (SDR role)
├── Post-sale implementation (CS role)
├── Deep technical architecture (SE role)
└── Legal contract review

Segments:
├── SMB AE: High volume, transactional
├── MM AE: Balanced, 30-60 day cycles
├── Enterprise AE: Complex, 90+ day cycles
└── Strategic AE: Named accounts, relationship-heavy
```

**SE (Sales Engineer/Solutions Consultant):**
```
Focus: Technical validation
Metrics: POC win rate, technical close rate
Reports to: SE Manager or Sales Manager

Responsibilities:
├── Technical discovery
├── Product demonstrations (deep dive)
├── POC/trial design and execution
├── RFP/security questionnaire response
├── Solution architecture
└── Technical objection handling

Coverage Models:
├── Dedicated: 1:1 with strategic AE
├── Paired: 1:2 or 1:3 with MM/Ent AEs
├── Pooled: Shared resource, assigned per deal
└── Specialized: By use case or vertical
```

**Sales Manager:**
```
Focus: Team performance
Metrics: Team quota attainment, rep development
Reports to: Director or VP Sales

Responsibilities:
├── Pipeline reviews (weekly)
├── Deal coaching and strategy
├── Forecast management
├── 1:1s and performance management
├── Hiring and onboarding
└── Process enforcement

Span of Control:
├── SDR Manager: 8-12 SDRs
├── SMB Manager: 8-10 AEs
├── MM Manager: 6-8 AEs
├── Enterprise Manager: 5-6 AEs
└── Strategic Manager: 4-5 AEs

Player/Coach vs. Pure Manager:
├── Player/Coach: Carries small quota, early stage
└── Pure Manager: No individual quota, scale stage
```

### Org Structure Models

**Model 1: Pod Structure**
```
┌─────────────────────────────────────────────────────────────┐
│                         POD                                 │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐      │
│   │  SDR 1  │  │  SDR 2  │  │  AE 1   │  │  AE 2   │      │
│   └─────────┘  └─────────┘  └─────────┘  └─────────┘      │
│                                                             │
│   ┌─────────┐  ┌─────────┐                                 │
│   │   SE    │  │   CSM   │  (Shared)                       │
│   └─────────┘  └─────────┘                                 │
│                                                             │
│   Pod Lead: AE 1 or Sales Manager                          │
└─────────────────────────────────────────────────────────────┘

Pros: Tight collaboration, clear ownership
Cons: Resource duplication, uneven workloads
Best for: Mid-market, balanced inbound/outbound
```

**Model 2: Functional Structure**
```
┌─────────────────────────────────────────────────────────────┐
│                      VP SALES                               │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐       │
│   │SDR Manager  │  │AE Manager   │  │SE Manager   │       │
│   │  └─SDR x8   │  │  └─AE x6    │  │  └─SE x4    │       │
│   └─────────────┘  └─────────────┘  └─────────────┘       │
│                                                             │
└─────────────────────────────────────────────────────────────┘

Pros: Specialization, clear career paths
Cons: Handoff friction, potential silos
Best for: Scale stage, 20+ rep orgs
```

**Model 3: Segment Structure**
```
┌─────────────────────────────────────────────────────────────┐
│                      VP SALES                               │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ┌──────────────────┐  ┌──────────────────┐                │
│  │  SMB Team        │  │  Enterprise Team │                │
│  │  └─Manager       │  │  └─Manager       │                │
│  │    └─SDR x4      │  │    └─SDR x2      │                │
│  │    └─AE x6       │  │    └─AE x4       │                │
│  │                  │  │    └─SE x2       │                │
│  └──────────────────┘  └──────────────────┘                │
│                                                             │
└─────────────────────────────────────────────────────────────┘

Pros: Tailored motions, focused expertise
Cons: Customer handoff when they grow, comp complexity
Best for: Distinct buyer journeys by segment
```

### SDR-to-AE Handoff

**Handoff Criteria:**
```
SDR books meeting, AE accepts if:
□ Decision-maker or influencer confirmed
□ Pain/use case documented
□ Basic qualification (BANT light)
□ Company meets ICP criteria
□ Meeting time works for both parties

SDR Passes to AE:
├── Company and contact info
├── Initial pain/challenge noted
├── How they found us
├── Relevant context from research
└── Any previous touch history
```

**Good Handoff:**
```
SDR Email to AE:

Subject: Meeting Confirmed - Acme Corp, Tuesday 2pm

Company: Acme Corp
Contact: Sarah Chen, VP Engineering
How Sourced: Outbound (LinkedIn + email sequence)

Context:
- 50-person engineering team
- Currently using manual deployment
- Pain: "Deployments take 4 hours and fail 30% of the time"
- She asked about CI/CD specifically
- Budget cycle: Q4

Prep:
- Acme raised Series B last month ($40M)
- Competitor ExampleCo is a customer (per their case study)
- Sarah was previously at TechCorp (our customer)

Meeting link attached. Let me know if you need anything!
```

**Bad Handoff:**
```
SDR Email to AE:

Subject: Meeting

I booked a meeting with someone at Acme. Tuesday at 2.
```

### Hiring Sequence

**What to Hire When:**

| ARR | Hire | Rationale |
|-----|------|-----------|
| $0-$500K | Founder sells | Founder must learn the sale |
| $500K-$1M | First AE | Prove another can sell |
| $1M-$2M | Second AE | Validate process, not luck |
| $2M | SDR | Feed AEs with pipeline |
| $2M-$3M | Third AE | Team is working |
| $3M-$5M | Sales Manager | Can't manage 5+ reps |
| $5M | CS/CSM | Protect revenue, enable expansion |
| $5M-$10M | SE | Technical sales support at scale |
| $10M | Sales Ops | Process, data, tools |
| $10M+ | Second Manager / Segments | Team too big for one manager |

### Good Org Design

```
$15M ARR SaaS - Well-Designed Org:

VP Sales (1)
├── SMB Team (Manager + 8 AEs + 4 SDRs)
│   └── Self-serve assisted, <$15K ACV
├── Mid-Market Team (Manager + 6 AEs + 3 SDRs + 2 SEs)
│   └── 30-60 day cycle, $15K-$75K ACV
├── Enterprise Team (Manager + 4 AEs + 2 SDRs + 2 SEs)
│   └── Named accounts, $75K+ ACV
└── Sales Ops (1)
    └── Tools, data, reporting

Total: 34 people

Rationale:
✓ Clear segment ownership
✓ Appropriate SDR:AE ratios
✓ SE coverage for technical sales
✓ Manageable spans
✓ Ops support for scale
```

### Bad Org Design

```
$15M ARR SaaS - Problematic Org:

VP Sales (1)
└── 25 AEs (all reporting to VP)
    └── No SDRs (AEs self-source)
    └── No SEs (AEs do their own demos)
    └── No segmentation (all accounts treated same)
    └── No Ops (VP does reporting in Excel)

Problems:
✗ VP can't manage 25 directs
✗ AEs wasting time on prospecting
✗ No technical support = shallow demos
✗ No segment focus = mediocre at everything
✗ No ops = chaotic data, bad forecasting
✗ No career path = AEs will leave
```

### Role Transition Planning

**SDR → AE Promotion Criteria:**
```
Quantitative:
├── 12+ months in SDR role
├── 3+ quarters at 100%+ of quota
├── Top 25% of SDR team

Qualitative:
├── Demonstrated deal sense (good handoffs)
├── Coachability and learning
├── Communication skills
├── Self-motivation

Process:
├── Internal posting / interest noted
├── Shadow program (3-5 deals)
├── Mock demo / discovery
├── Interview panel
└── Offer + ramp plan
```

### Anti-Patterns

- **Founder can't let go** — Stays in every deal too long
- **Flat org at scale** — 15+ reps to one manager
- **Skipping the SDR** — AEs cold calling, wasting time
- **Hybrid everything** — AE does SDR, SE, and CSM work
- **Segment confusion** — No clear rules on who owns what
- **Promote top reps** — Best AE ≠ best manager
- **Title inflation** — Everyone is "Senior" or "Director"
