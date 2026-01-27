---
name: skill-creator
description: Create new Claude Code skills with proper structure, frontmatter, and organization. Use when asked to "create a skill", "make a skill", "build a skill", or when designing expertise modules for Claude Code.
---

# Skill Creator

Expert guidance for creating Claude Code skills — reusable expertise modules that enhance Claude's capabilities.

## What is a Skill?

A skill is a markdown-based knowledge module that Claude loads when invoked. Skills provide:

- **Domain expertise** — Deep knowledge in a specific area
- **Consistent patterns** — Reusable rules and guidelines
- **Contextual guidance** — Applied automatically when relevant

## Skill Structure

### Minimal (Single File)
```
skills/
└── my-skill/
    └── SKILL.md       # Required: frontmatter + content
```

### Standard (With Rules)
```
skills/
└── my-skill/
    ├── SKILL.md       # Required: overview + how to use
    ├── metadata.json  # Optional: version, org, references
    └── rules/         # Optional: individual guidelines
        ├── _sections.md
        ├── category-rule-name.md
        └── ...
```

## SKILL.md Format

```yaml
---
name: my-skill-name           # kebab-case, unique identifier
description: When and why to use this skill. Include trigger phrases
             like "use when", "use for", or specific keywords.
argument-hint: <optional>     # If skill accepts arguments
---

# Skill Title

Brief description of what this skill provides.

## How This Skill Works

Explain what happens when invoked.

## Core Concepts

Key frameworks, principles, or knowledge areas.
```

## Rule File Format

```yaml
---
title: Rule Title
impact: CRITICAL | HIGH | MEDIUM-HIGH | MEDIUM | LOW
tags: category, related, topics
---

## Rule Title

**Impact: LEVEL**

Explanation of the rule.

### Good Example
\`\`\`
code or content
\`\`\`

### Bad Example
\`\`\`
anti-pattern
\`\`\`

### Checklist
- [ ] Actionable items
```

## Skill Types

| Type | Structure | Use When |
|------|-----------|----------|
| **Reference** | Rules directory with 10+ files | Large knowledge base (style guides, best practices) |
| **Procedural** | Single SKILL.md with steps | Workflow or process guidance |
| **Constraints** | SKILL.md with MUST/NEVER rules | Opinionated guardrails |
| **Domain Expert** | SKILL.md + key concepts | Specialized knowledge area |

## Naming Conventions

- **Skill name:** `kebab-case`, descriptive (e.g., `senior-product-marketer`)
- **Rule files:** `category-rule-name.md` (e.g., `trial-value-proposition.md`)
- **Special files:** Prefix with `_` (e.g., `_sections.md`, `_template.md`)

## Description Best Practices

The `description` field determines when Claude suggests the skill. Include:

1. **Primary use case** — "Expert guidance for X"
2. **Trigger phrases** — "Use when writing", "Use for", "Use when asked to"
3. **Keywords** — Specific terms that should trigger the skill

```yaml
# Good
description: Expert product marketing guidance for SaaS growth - trial
             acquisition, user activation, and freemium conversion. Use
             when writing landing pages, onboarding flows, or pricing pages.

# Bad
description: Marketing stuff.
```

## Impact Levels

| Level | Meaning | When to Use |
|-------|---------|-------------|
| CRITICAL | Must always apply | Core principles, major outcomes |
| HIGH | Should usually apply | Important patterns |
| MEDIUM-HIGH | Apply when relevant | Good practices |
| MEDIUM | Apply when feasible | Helpful suggestions |
| LOW | Nice to have | Micro-optimizations |

## Anti-Patterns

1. **Too broad** — "A skill for everything about code" → Split into focused skills
2. **No examples** — Guidelines without good/bad examples are hard to apply
3. **Feature lists** — Skills should teach *how*, not just *what*
4. **No trigger phrases** — Description must help Claude know when to use it
5. **Duplicate knowledge** — Check existing skills before creating new ones

## Creating a New Skill

1. **Define the expertise** — What specific knowledge does this encode?
2. **Choose structure** — Single file for simple, rules directory for complex
3. **Write description** — Include trigger phrases and keywords
4. **Add examples** — Good/bad patterns for each guideline
5. **Test invocation** — Verify Claude loads it for expected prompts
