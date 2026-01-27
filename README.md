```
  ____  _             _                    ___  ____
 / ___|| |_ __ _ _ __| |_ _   _ _ __      / _ \/ ___|
 \___ \| __/ _` | '__| __| | | | '_ \    | | | \___ \
  ___) | || (_| | |  | |_| |_| | |_) |   | |_| |___) |
 |____/ \__\__,_|_|   \__|\__,_| .__/     \___/|____/
                               |_|
```

# Startup OS Skills

A comprehensive collection of **51 AI agent skills** for building and scaling startups — reusable expertise modules covering sales, marketing, product, customer success, and video production.

[![Skills](https://img.shields.io/badge/skills-51-blue)](https://skills.sh)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

## Quick Start

Install all skills with one command:

```bash
npx skills add ncklrs/startup-os-skills
```

Select the skills you want to install, and they'll be added to your AI coding agent (Claude Code, Cursor, Windsurf, etc.).

### Install Specific Skills

```bash
# Install and select interactively
npx skills add ncklrs/startup-os-skills

# List available skills without installing
npx skills add ncklrs/startup-os-skills --list
```

---

## What are Skills?

Skills are markdown-based knowledge modules that AI agents load when invoked. They provide:

- **Domain expertise** — Deep knowledge in specific areas (sales, marketing, product, etc.)
- **Consistent patterns** — Reusable rules and guidelines
- **Contextual guidance** — Applied automatically when relevant
- **Trigger phrases** — Agents know when to activate each skill

### How Skills Work

```
┌─────────────────────────────────────────────────────────────────┐
│  User: "Help me write a discovery call script"                  │
├─────────────────────────────────────────────────────────────────┤
│  Agent detects: "discovery call" → loads discovery-caller skill │
├─────────────────────────────────────────────────────────────────┤
│  Skill provides: SPIN framework, qualification questions,       │
│                  pain identification templates, examples        │
├─────────────────────────────────────────────────────────────────┤
│  Agent responds with expert-level discovery call guidance       │
└─────────────────────────────────────────────────────────────────┘
```

---

## Skills Overview

| Category | Skills | Parent Skill |
|----------|--------|--------------|
| [Sales](#sales-9-skills) | 9 | `sales-leader` |
| [Marketing](#marketing-14-skills) | 14 | `marketing-strategist` |
| [Product](#product-9-skills) | 9 | `product-leader` |
| [Customer Success](#customer-success-6-skills) | 6 | `cs-strategist` |
| [Video Production](#video-production-13-skills) | 13 | `remotion-asset-coordinator` |
| **Total** | **51** | |

---

## Sales (9 skills)

**Parent Skill:** [`sales-leader`](skills/sales-leader) — Strategic sales leadership for B2B SaaS

Complete sales expertise from strategy through execution.

| Skill | Description | Use When |
|-------|-------------|----------|
| [`sales-strategist`](skills/sales-strategist) | Sales methodology, territory planning, pipeline strategy | Designing sales processes, improving win rates |
| [`account-executive`](skills/account-executive) | Full-cycle enterprise sales, account management | Running complex deals, managing accounts |
| [`discovery-caller`](skills/discovery-caller) | Discovery frameworks, MEDDPICC, pain identification | Preparing for discovery calls, qualifying leads |
| [`demo-specialist`](skills/demo-specialist) | Demo preparation, storytelling, objection handling | Creating product demos, handling objections |
| [`proposal-writer`](skills/proposal-writer) | Proposal structure, executive summaries, RFP responses | Writing proposals, responding to RFPs |
| [`sales-negotiator`](skills/sales-negotiator) | Negotiation tactics, discount strategy, contract terms | Negotiating deals, handling pricing objections |
| [`sales-enablement`](skills/sales-enablement) | Sales training, playbooks, onboarding | Building sales training, creating playbooks |
| [`sales-ops-analyst`](skills/sales-ops-analyst) | CRM optimization, pipeline analytics, comp plans | Optimizing sales operations, building dashboards |

### Sales Skill Architecture

```
                    ┌─────────────────┐
                    │  sales-leader   │  ← Strategic oversight
                    └────────┬────────┘
                             │
        ┌────────────────────┼────────────────────┐
        │                    │                    │
        ▼                    ▼                    ▼
┌───────────────┐    ┌───────────────┐    ┌───────────────┐
│   STRATEGY    │    │   EXECUTION   │    │  OPERATIONS   │
├───────────────┤    ├───────────────┤    ├───────────────┤
│sales-strategist│   │discovery-caller│   │sales-ops-     │
│               │    │demo-specialist │    │analyst        │
│               │    │proposal-writer │    │sales-         │
│               │    │sales-negotiator│    │enablement     │
│               │    │account-        │    │               │
│               │    │executive       │    │               │
└───────────────┘    └───────────────┘    └───────────────┘
```

---

## Marketing (14 skills)

**Parent Skill:** [`marketing-strategist`](skills/marketing-strategist) — Strategic marketing leadership for B2B SaaS

Complete marketing expertise covering the full funnel.

### Strategy & Leadership

| Skill | Description | Use When |
|-------|-------------|----------|
| [`gtm-leader`](skills/gtm-leader) | GTM strategy, positioning, brand building | Planning go-to-market, market entry |
| [`competitive-strategist`](skills/competitive-strategist) | Win/loss analysis, battlecards, market intelligence | Competitive analysis, positioning |
| [`pricing-strategist`](skills/pricing-strategist) | Pricing psychology, packaging, value metrics | Setting pricing, packaging products |

### Acquisition & Growth

| Skill | Description | Use When |
|-------|-------------|----------|
| [`performance-marketer`](skills/performance-marketer) | Paid acquisition, CRO, landing pages, A/B testing | Running paid campaigns, optimizing conversion |
| [`seo-content-strategist`](skills/seo-content-strategist) | Keyword research, content clusters, technical SEO | SEO strategy, content planning |
| [`senior-product-marketer`](skills/senior-product-marketer) | Trial acquisition, value propositions, launches | Product launches, messaging |

### Content & Copy

| Skill | Description | Use When |
|-------|-------------|----------|
| [`gtm-copywriter`](skills/gtm-copywriter) | Email, content, and social media copywriting | Writing marketing copy |
| [`website-copy-specialist`](skills/website-copy-specialist) | Homepage, feature pages, pricing pages | Writing website copy |
| [`pr-specialist`](skills/pr-specialist) | Press releases, media pitches, analyst relations | PR campaigns, media outreach |

### Customer & Community

| Skill | Description | Use When |
|-------|-------------|----------|
| [`customer-lifecycle-marketer`](skills/customer-lifecycle-marketer) | Retention, expansion, advocacy, win-back | Lifecycle campaigns, retention |
| [`community-builder`](skills/community-builder) | Community-led growth, Discord/Slack, DevRel | Building communities |

### Channels & Events

| Skill | Description | Use When |
|-------|-------------|----------|
| [`partnership-marketer`](skills/partnership-marketer) | Co-marketing, integrations, affiliate programs | Partner programs |
| [`event-marketer`](skills/event-marketer) | Conferences, webinars, field marketing | Event planning |

### Marketing Funnel Coverage

```
  AWARENESS          CONSIDERATION         CONVERSION          RETENTION           ADVOCACY
      │                    │                   │                   │                   │
      ▼                    ▼                   ▼                   ▼                   ▼
┌───────────┐       ┌─────────────┐     ┌───────────┐      ┌───────────────┐   ┌─────────────┐
│gtm-leader │       │performance- │     │senior-    │      │customer-      │   │community-   │
│pr-        │       │marketer     │     │product-   │      │lifecycle-     │   │builder      │
│specialist │       │seo-content- │     │marketer   │      │marketer       │   │             │
│event-     │       │strategist   │     │pricing-   │      │               │   │             │
│marketer   │       │             │     │strategist │      │               │   │             │
└───────────┘       └─────────────┘     └───────────┘      └───────────────┘   └─────────────┘
                                              │
                    ┌─────────────────────────┴─────────────────────────┐
                    │                  SUPPORT SKILLS                   │
                    ├───────────────┬──────────────────┬────────────────┤
                    │gtm-copywriter │website-copy-     │competitive-    │
                    │               │specialist        │strategist      │
                    │               │                  │partnership-    │
                    │               │                  │marketer        │
                    └───────────────┴──────────────────┴────────────────┘
```

---

## Product (9 skills)

**Parent Skill:** [`product-leader`](skills/product-leader) — Strategic product leadership for SaaS

Complete product management expertise from strategy through launch.

| Skill | Description | Use When |
|-------|-------------|----------|
| [`product-strategist`](skills/product-strategist) | Product vision, roadmap strategy, positioning | Defining product strategy |
| [`product-manager`](skills/product-manager) | Feature development, sprint planning, stakeholders | Day-to-day PM work |
| [`product-discovery`](skills/product-discovery) | User research, opportunity assessment, validation | Running discovery, research |
| [`product-specs-writer`](skills/product-specs-writer) | PRDs, user stories, acceptance criteria | Writing specs, PRDs |
| [`product-analyst`](skills/product-analyst) | Product analytics, funnel analysis, experimentation | Analyzing metrics, A/B tests |
| [`product-launch-manager`](skills/product-launch-manager) | Launch planning, GTM coordination, releases | Planning launches |
| [`growth-product-manager`](skills/growth-product-manager) | Growth loops, activation, retention, monetization | Growth experiments |
| [`platform-product-manager`](skills/platform-product-manager) | API strategy, developer experience, ecosystems | Platform/API products |

### Product Lifecycle Coverage

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         PRODUCT LIFECYCLE                                    │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   DISCOVER              DEFINE              BUILD              LAUNCH       │
│       │                    │                   │                   │        │
│       ▼                    ▼                   ▼                   ▼        │
│  ┌─────────┐         ┌─────────┐         ┌─────────┐         ┌─────────┐   │
│  │product- │         │product- │         │product- │         │product- │   │
│  │discovery│         │specs-   │         │manager  │         │launch-  │   │
│  │         │         │writer   │         │         │         │manager  │   │
│  │product- │         │product- │         │product- │         │         │   │
│  │strategist│        │strategist│        │analyst  │         │         │   │
│  └─────────┘         └─────────┘         └─────────┘         └─────────┘   │
│                                                                             │
│   SPECIALIZED: growth-product-manager │ platform-product-manager            │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Customer Success (6 skills)

**Parent Skill:** [`cs-strategist`](skills/cs-strategist) — Strategic CS leadership for org design, segmentation, and metrics

Complete customer success expertise from onboarding through renewal.

| Skill | Description | Use When |
|-------|-------------|----------|
| [`onboarding-specialist`](skills/onboarding-specialist) | Onboarding programs, time-to-value, implementation | Designing onboarding |
| [`customer-health-analyst`](skills/customer-health-analyst) | Health scoring, churn prediction, usage analytics | Building health scores |
| [`support-operations`](skills/support-operations) | Ticket management, SLAs, knowledge base, QA | Support process design |
| [`qbr-facilitator`](skills/qbr-facilitator) | QBR programs, executive preparation, value demos | Running QBRs |
| [`renewal-manager`](skills/renewal-manager) | Renewal forecasting, save plays, expansion | Managing renewals |

### Customer Journey Coverage

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                       CUSTOMER JOURNEY                                       │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ONBOARD             ADOPT               EXPAND              RENEW         │
│       │                 │                    │                   │          │
│       ▼                 ▼                    ▼                   ▼          │
│  ┌──────────┐     ┌──────────┐        ┌──────────┐        ┌──────────┐     │
│  │onboarding│     │customer- │        │qbr-      │        │renewal-  │     │
│  │specialist│     │health-   │        │facilitator│       │manager   │     │
│  │          │     │analyst   │        │          │        │          │     │
│  └──────────┘     └──────────┘        └──────────┘        └──────────┘     │
│                         │                                                   │
│                         ▼                                                   │
│                  ┌──────────────┐                                           │
│                  │support-      │  ← Throughout journey                     │
│                  │operations    │                                           │
│                  └──────────────┘                                           │
│                                                                             │
│   STRATEGIC OVERSIGHT: cs-strategist                                        │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Video Production (13 skills)

**Parent Skill:** [`remotion-asset-coordinator`](skills/remotion-asset-coordinator) — Asset management for Remotion video projects

Complete video creation pipeline from concept to render, built around [Remotion](https://remotion.dev).

| Skill | Description | Use When |
|-------|-------------|----------|
| [`create-video-start`](skills/create-video-start) | Master orchestrator for video creation | Starting new video projects |
| [`motion-designer`](skills/motion-designer) | Scene composition, timing, transitions | Designing motion graphics |
| [`vsl-storyboard-writer`](skills/vsl-storyboard-writer) | Video sales letter storyboards | Creating VSL scripts |
| [`remotion-best-practices`](skills/remotion-best-practices) | Core Remotion patterns | Any Remotion development |
| [`remotion-scaffold`](skills/remotion-scaffold) | Project structure, file organization | Setting up Remotion projects |
| [`remotion-spec-translator`](skills/remotion-spec-translator) | Convert motion specs to code | Implementing designs |
| [`remotion-component-gen`](skills/remotion-component-gen) | Generate scene components | Building video scenes |
| [`remotion-composition`](skills/remotion-composition) | Sequence ordering, transitions | Structuring videos |
| [`remotion-animation`](skills/remotion-animation) | Spring configs, interpolations | Animation fine-tuning |
| [`remotion-render-config`](skills/remotion-render-config) | Output settings, codec, format | Rendering videos |
| [`remotion-performance-optimizer`](skills/remotion-performance-optimizer) | Performance analysis | Optimizing slow videos |
| [`remotion-video-reviewer`](skills/remotion-video-reviewer) | Review for spec compliance | Quality assurance |

### Video Production Pipeline

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                      VIDEO PRODUCTION PIPELINE                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   CONCEPT           DESIGN            BUILD             RENDER              │
│       │                │                 │                  │               │
│       ▼                ▼                 ▼                  ▼               │
│  ┌──────────┐    ┌──────────┐     ┌───────────┐     ┌───────────┐          │
│  │vsl-      │    │motion-   │     │remotion-  │     │remotion-  │          │
│  │storyboard│    │designer  │     │scaffold   │     │render-    │          │
│  │-writer   │    │          │     │remotion-  │     │config     │          │
│  │          │    │          │     │spec-      │     │remotion-  │          │
│  │          │    │          │     │translator │     │performance│          │
│  │          │    │          │     │remotion-  │     │-optimizer │          │
│  │          │    │          │     │component- │     │remotion-  │          │
│  │          │    │          │     │gen        │     │video-     │          │
│  │          │    │          │     │remotion-  │     │reviewer   │          │
│  │          │    │          │     │composition│     │           │          │
│  │          │    │          │     │remotion-  │     │           │          │
│  │          │    │          │     │animation  │     │           │          │
│  └──────────┘    └──────────┘     └───────────┘     └───────────┘          │
│                                                                             │
│   ORCHESTRATION: create-video-start                                         │
│   ASSETS: remotion-asset-coordinator                                        │
│   PATTERNS: remotion-best-practices                                         │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Skill Structure

Each skill follows the [Agent Skills specification](https://agentskills.io/specification):

```
skill-name/
├── SKILL.md           # Required: instructions for the agent
├── rules/             # Optional: detailed guidelines
│   ├── _sections.md   # Rule organization
│   └── *.md           # Individual rule files
└── references/        # Optional: supporting documentation
```

### SKILL.md Format

```yaml
---
name: skill-name          # Lowercase, hyphens only, matches directory
description: >
  What this skill does and when to use it.
  Include trigger phrases like "Use when..." and "Use for...".
---

# Skill Title

Instructions and guidance for the agent...
```

### Impact Levels

Rules are tagged by impact:

| Level | Meaning |
|-------|---------|
| **CRITICAL** | Must always apply — core principles |
| **HIGH** | Should usually apply — important patterns |
| **MEDIUM-HIGH** | Apply when relevant — good practices |
| **MEDIUM** | Apply when feasible — helpful suggestions |
| **LOW** | Nice to have — micro-optimizations |

---

## Alternative Installation

### Manual Installation

Copy skills directly to your agent's skills folder:

```bash
# Clone the repo
git clone https://github.com/ncklrs/startup-os-skills.git

# Copy specific skills
cp -r startup-os-skills/skills/discovery-caller ~/.claude/skills/

# Or symlink for easy updates
ln -s $(pwd)/startup-os-skills/skills/discovery-caller ~/.claude/skills/
```

### Agent-Specific Paths

| Agent | Skills Path |
|-------|-------------|
| Claude Code | `~/.claude/skills/` |
| Cursor | `.cursor/skills/` |
| Windsurf | `.windsurf/skills/` |

---

## Roadmap

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           STARTUP OS SKILLS                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ✅ PHASE 1 - Core Revenue Engine (51 skills)                               │
│     Sales (9) │ Marketing (14) │ Product (9) │ CS (6) │ Video (13)          │
│                                                                             │
│  ⏳ PHASE 2 - Operations & Finance                                          │
│     Finance │ Legal │ People/HR │ Operations                                │
│                                                                             │
│  ⏳ PHASE 3 - Engineering & Technical                                       │
│     Engineering │ Security │ Data │ Infrastructure                          │
│                                                                             │
│  ⏳ PHASE 4 - Strategy & Growth                                             │
│     Strategy │ Fundraising │ M&A │ Board Management                         │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Contributing

### Adding a New Skill

1. Create a directory in `skills/` with your skill name (kebab-case)
2. Add `SKILL.md` with required frontmatter:
   ```yaml
   ---
   name: your-skill-name
   description: What this skill does. Use when [triggers]. Use for [keywords].
   ---
   ```
3. Add rules in `rules/` directory if needed
4. Include good/bad examples in each rule

### Skill Guidelines

- **Focused** — One skill, one domain
- **Actionable** — Clear guidance, not just theory
- **Examples** — Good/bad patterns for every guideline
- **Trigger phrases** — Help agents know when to activate

---

## License

MIT

---

<p align="center">
  <sub>Built for AI coding agents • Compatible with <a href="https://skills.sh">skills.sh</a></sub>
</p>
