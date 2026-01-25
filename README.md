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

### Marketing (5 skills, 52 rules)

Full-funnel marketing expertise from awareness through advocacy.

| Skill | Description | Rules |
|-------|-------------|-------|
| [`gtm-leader`](marketing/gtm-leader) | Strategic GTM planning, positioning, brand building, platform tactics | 14 |
| [`gtm-copywriter`](marketing/gtm-copywriter) | Email, content, and social media copywriting | 12 |
| [`senior-product-marketer`](marketing/senior-product-marketer) | Trial acquisition, value propositions, conversion optimization | 5 |
| [`performance-marketer`](marketing/performance-marketer) | Paid acquisition, CRO, landing pages, A/B testing, analytics | 11 |
| [`customer-lifecycle-marketer`](marketing/customer-lifecycle-marketer) | Retention, expansion, advocacy, referrals, win-back | 10 |

```
Awareness → Consideration → Trial → Activation → Retention → Expansion → Advocacy
    │            │           │          │            │           │          │
gtm-leader  gtm-copywriter  senior-   customer-lifecycle-marketer ─────────┘
                            product-
                            marketer
```

---

### Video Production (13 skills)

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

### Development (4 skills)

Best practices for modern web development.

| Skill | Description |
|-------|-------------|
| [`vercel-react-best-practices`](vercel-react-best-practices) | React and Next.js performance optimization from Vercel Engineering |
| [`stripe-best-practices`](stripe-best-practices) | Stripe integration patterns for payments, subscriptions, webhooks |
| [`ui-skills`](ui-skills) | Opinionated constraints for building better interfaces |
| [`web-design-guidelines`](web-design-guidelines) | Web Interface Guidelines compliance and accessibility |

---

### Documentation & Tooling (2 skills)

| Skill | Description |
|-------|-------------|
| [`github-wiki-docs`](github-wiki-docs) | Changelog and GitHub wiki documentation patterns |
| [`skill-creator`](skill-creator) | Create new Claude Code skills with proper structure |

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
