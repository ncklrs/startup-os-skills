---
title: Frontmatter Requirements
impact: CRITICAL
tags: content, frontmatter, metadata
---

## Frontmatter Requirements

**Impact: CRITICAL**

Frontmatter is required in SKILL.md and optional in rule files.

### SKILL.md Frontmatter (Required)

```yaml
---
name: skill-name              # Required: kebab-case identifier
description: Trigger phrases  # Required: when to use this skill
argument-hint: <pattern>      # Optional: expected arguments
---
```

### Rule File Frontmatter (Recommended)

```yaml
---
title: Rule Title             # Human-readable name
impact: HIGH                  # CRITICAL/HIGH/MEDIUM-HIGH/MEDIUM/LOW
impactDescription: 20% gain   # Optional: quantified impact
tags: category, topic         # For cross-referencing
---
```

### Description Field

The most important field. Determines when Claude loads the skill.

**Include:**
- Primary use case
- Trigger phrases ("use when", "use for")
- Keywords that should activate the skill

```yaml
# Good — specific triggers
description: Review UI code for accessibility compliance. Use when asked
             to "check accessibility", "audit design", or "review UX".

# Bad — vague, no triggers
description: Helps with UI stuff.
```

### Name Field

- Use kebab-case: `senior-product-marketer`
- Be descriptive: `react-performance-patterns` not `react-stuff`
- Unique across all skills

### Anti-Pattern

Missing or generic description means Claude won't know when to suggest the skill.
