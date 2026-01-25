```
  ____  _             _                    ___  ____
 / ___|| |_ __ _ _ __| |_ _   _ _ __      / _ \/ ___|
 \___ \| __/ _` | '__| __| | | | '_ \    | | | \___ \
  ___) | || (_| | |  | |_| |_| | |_) |   | |_| |___) |
 |____/ \__\__,_|_|   \__|\__,_| .__/     \___/|____/
                               |_|
```

# Startup OS

A comprehensive collection of Claude Code skills for building and scaling startups — reusable expertise modules covering every function from sales to engineering.

## What are Skills?

Skills are markdown-based knowledge modules that Claude loads when invoked. They provide:

- **Domain expertise** — Deep knowledge in specific areas
- **Consistent patterns** — Reusable rules and guidelines
- **Contextual guidance** — Applied automatically when relevant

## Installation

Copy any skill directory to your Claude Code skills folder:

```bash
# Copy a single skill
cp -r marketing/gtm-copywriter ~/.claude/skills/

# Or symlink for easy updates
ln -s $(pwd)/marketing/gtm-copywriter ~/.claude/skills/gtm-copywriter
```

---

## Skills by Category

### Sales (8 skills)

Complete sales expertise from strategy through operations.

| Skill | Description |
|-------|-------------|
| [`sales-strategist`](sales/sales-strategist) | Sales methodology, territory planning, pipeline strategy, win rates |
| [`discovery-caller`](sales/discovery-caller) | Discovery frameworks, qualification, pain identification, MEDDIC |
| [`demo-specialist`](sales/demo-specialist) | Demo preparation, storytelling, objection handling, technical demos |
| [`proposal-writer`](sales/proposal-writer) | Proposal structure, executive summaries, pricing presentation, RFP responses |
| [`sales-negotiator`](sales/sales-negotiator) | Negotiation tactics, discount strategy, multi-party deals, contract terms |
| [`account-executive`](sales/account-executive) | Full-cycle sales, account management, quota attainment, forecasting |
| [`sales-enablement`](sales/sales-enablement) | Sales training, playbooks, content, onboarding, tool adoption |
| [`sales-ops-analyst`](sales/sales-ops-analyst) | CRM optimization, pipeline analytics, territory design, comp plans |

---

### Product (8 skills)

Complete product management expertise from strategy through launch.

| Skill | Description |
|-------|-------------|
| [`product-strategist`](product/product-strategist) | Product vision, roadmap strategy, market positioning, portfolio management |
| [`product-discovery`](product/product-discovery) | User research, opportunity assessment, problem validation, prototyping |
| [`product-manager`](product/product-manager) | Feature development, sprint planning, stakeholder management, metrics |
| [`product-specs-writer`](product/product-specs-writer) | PRDs, user stories, acceptance criteria, technical specs |
| [`product-analyst`](product/product-analyst) | Product analytics, funnel analysis, experimentation, data-driven decisions |
| [`product-launch-manager`](product/product-launch-manager) | Launch planning, GTM coordination, beta programs, release management |
| [`growth-product-manager`](product/growth-product-manager) | Growth loops, activation, retention, monetization, experimentation |
| [`platform-product-manager`](product/platform-product-manager) | API strategy, developer experience, platform ecosystems, integrations |

---

### Customer Success (6 skills)

Complete customer success expertise from onboarding through renewal.

| Skill | Description |
|-------|-------------|
| [`cs-strategist`](customer-success) | CS org design, segmentation, metrics, playbooks, technology stack |
| [`onboarding-specialist`](customer-success/onboarding-specialist) | Onboarding programs, time-to-value, implementation, training delivery |
| [`customer-health-analyst`](customer-success/customer-health-analyst) | Health scoring, churn prediction, usage analytics, cohort analysis |
| [`support-operations`](customer-success/support-operations) | Ticket management, SLAs, tier structure, knowledge base, quality assurance |
| [`qbr-facilitator`](customer-success/qbr-facilitator) | QBR programs, executive preparation, value demonstration, strategic planning |
| [`renewal-manager`](customer-success/renewal-manager) | Renewal forecasting, playbooks, save plays, expansion, contract negotiation |

---

### Marketing (13 skills)

Complete marketing expertise covering the full funnel from awareness through advocacy.

#### Strategy & Leadership
| Skill | Description |
|-------|-------------|
| [`gtm-leader`](marketing/gtm-leader) | Strategic GTM planning, positioning, brand building, platform tactics |
| [`competitive-strategist`](marketing/competitive-strategist) | Win/loss analysis, battlecards, market intelligence, competitive positioning |
| [`pricing-strategist`](marketing/pricing-strategist) | Pricing psychology, packaging, value metrics, enterprise pricing |

#### Acquisition & Growth
| Skill | Description |
|-------|-------------|
| [`performance-marketer`](marketing/performance-marketer) | Paid acquisition, CRO, landing pages, A/B testing, analytics |
| [`seo-content-strategist`](marketing/seo-content-strategist) | Keyword research, content clusters, technical SEO, link building |
| [`senior-product-marketer`](marketing/senior-product-marketer) | Trial acquisition, value propositions, conversion optimization |

#### Content & Copy
| Skill | Description |
|-------|-------------|
| [`gtm-copywriter`](marketing/gtm-copywriter) | Email, content, and social media copywriting |
| [`website-copy-specialist`](marketing/website-copy-specialist) | Homepage, feature pages, pricing pages, comparison pages |
| [`pr-specialist`](marketing/pr-specialist) | Press releases, media pitches, crisis comms, analyst relations |

#### Customer & Community
| Skill | Description |
|-------|-------------|
| [`customer-lifecycle-marketer`](marketing/customer-lifecycle-marketer) | Retention, expansion, advocacy, referrals, win-back |
| [`community-builder`](marketing/community-builder) | Community-led growth, Discord/Slack, ambassador programs, DevRel |

#### Channels & Events
| Skill | Description |
|-------|-------------|
| [`partnership-marketer`](marketing/partnership-marketer) | Co-marketing, integrations marketplace, affiliate programs, channel partners |
| [`event-marketer`](marketing/event-marketer) | Conferences, webinars, virtual events, field marketing |

```
                            ┌─────────────────────────────────────┐
                            │         MARKETING FUNNEL            │
                            └─────────────────────────────────────┘

  AWARENESS          CONSIDERATION         CONVERSION          RETENTION           ADVOCACY
      │                    │                   │                   │                   │
      ▼                    ▼                   ▼                   ▼                   ▼
┌───────────┐       ┌─────────────┐     ┌───────────┐      ┌───────────────┐   ┌─────────────┐
│gtm-leader │       │performance- │     │senior-    │      │customer-      │   │community-   │
│pr-         │       │marketer     │     │product-   │      │lifecycle-     │   │builder      │
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

### Video Production (12 skills)

Complete video creation pipeline from concept to render, built around Remotion.

| Skill | Description |
|-------|-------------|
| [`motion-designer`](video/motion-designer) | Professional motion design with scene composition, timing, transitions |
| [`vsl-storyboard-writer`](video/vsl-storyboard-writer) | Video sales letter and product marketing storyboards |
| [`remotion-best-practices`](video/remotion-best-practices) | Core Remotion patterns for animations, assets, audio, timing |
| [`remotion-scaffold`](video/remotion-scaffold) | Project structure and file organization |
| [`remotion-spec-translator`](video/remotion-spec-translator) | Convert motion specs to Remotion code |
| [`remotion-component-gen`](video/remotion-component-gen) | Generate scene components from visual direction |
| [`remotion-composition`](video/remotion-composition) | Sequence ordering and scene transitions |
| [`remotion-animation`](video/remotion-animation) | Spring configs, interpolations, easing functions |
| [`remotion-render-config`](video/remotion-render-config) | Output settings, codec, format, quality |
| [`remotion-performance-optimizer`](video/remotion-performance-optimizer) | Performance analysis and optimization |
| [`remotion-video-reviewer`](video/remotion-video-reviewer) | Review implementations for spec compliance |
| [`create-video-start`](video/create-video-start) | Master orchestrator for video creation pipeline |

---

## Startup OS Roadmap

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           STARTUP OS SKILLS                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ✅ PHASE 1 - Core Revenue Engine (22 skills)                               │
│     Sales (8) │ Product (8) │ Customer Success (6)                          │
│                                                                             │
│  ⏳ PHASE 2 - Operations & Finance                                          │
│     Finance │ Legal │ People/HR                                             │
│                                                                             │
│  ⏳ PHASE 3 - Engineering & Technical                                       │
│     Engineering │ Security │ Data                                           │
│                                                                             │
│  ⏳ PHASE 4 - Strategy & Growth                                             │
│     Strategy │ Fundraising │ M&A                                            │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Skill Structure

Each skill follows a consistent structure:

```
skill-name/
├── SKILL.md           # Required: overview, philosophy, how to use
├── metadata.json      # Optional: version, references
└── rules/             # Optional: individual guidelines
    ├── _sections.md   # Rule organization and impact levels
    ├── category-rule-name.md
    └── ...
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

## Contributing

### Adding a New Skill

1. Create a directory with your skill name (kebab-case)
2. Add `SKILL.md` with frontmatter:
   ```yaml
   ---
   name: your-skill-name
   description: When and why to use this skill. Include trigger phrases.
   ---
   ```
3. Add rules in `rules/` directory if needed
4. Include good/bad examples in each rule

### Skill Guidelines

- **Focused** — One skill, one domain
- **Actionable** — Clear guidance, not just theory
- **Examples** — Good/bad patterns for every guideline
- **Trigger phrases** — Help Claude know when to use it

---

## License

MIT

---

<p align="center">
  <sub>Built for <a href="https://claude.ai/code">Claude Code</a></sub>
</p>
