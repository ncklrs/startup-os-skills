---
title: Constraints Skill Pattern
impact: MEDIUM
tags: patterns, skill-types
---

## Constraints Skill Pattern

**Impact: MEDIUM**

For encoding opinionated guardrails with MUST/NEVER rules.

### When to Use

- Style guides and conventions
- Architectural decisions
- Compliance requirements
- Opinionated best practices

### Structure

Single SKILL.md with clear MUST/MUST NOT/NEVER rules.

### Example Format

```markdown
---
name: ui-constraints
description: Opinionated constraints for building interfaces.
             Use when creating UI components or reviewing frontend code.
---

# UI Constraints

When building interfaces, apply these constraints:

## Stack
- MUST use Tailwind CSS defaults
- MUST use accessible component primitives
- NEVER mix component libraries

## Components
- MUST have single responsibility
- MUST be keyboard navigable
- NEVER use `onClick` on non-interactive elements

## Styling
- MUST use design tokens
- NEVER use arbitrary values (e.g., `text-[13px]`)
- MUST support dark mode
```

### Rule Prefixes

| Prefix | Meaning |
|--------|---------|
| MUST | Required, no exceptions |
| SHOULD | Strongly recommended |
| MAY | Optional but allowed |
| MUST NOT | Prohibited |
| NEVER | Prohibited, emphasized |

### What Makes It Work

- **Clear authority** — Rules, not suggestions
- **No ambiguity** — MUST/NEVER leaves no room for interpretation
- **Scannable** — Easy to check compliance

### Anti-Pattern

Don't mix constraints with explanatory content. Constraints should be checkable, not debatable.
