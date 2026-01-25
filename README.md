```
   _____ _                 _        _____ _    _ _ _
  / ____| |               | |      / ____| |  (_) | |
 | |    | | __ _ _   _  __| | ___ | (___ | | ___| | |___
 | |    | |/ _` | | | |/ _` |/ _ \ \___ \| |/ / | | / __|
 | |____| | (_| | |_| | (_| |  __/ ____) |   <| | | \__ \
  \_____|_|\__,_|\__,_|\__,_|\___||_____/|_|\_\_|_|_|___/

```

# Claude Skills Collection

A curated collection of Claude Code skills — reusable expertise modules that enhance Claude's capabilities for specialized tasks.

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
