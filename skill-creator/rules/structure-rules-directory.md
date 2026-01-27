---
title: Rules Directory Structure
impact: HIGH
tags: structure, organization, scaling
---

## Rules Directory Structure

**Impact: HIGH**

For large skill sets, organize guidelines into individual rule files.

### Directory Structure

```
~/.claude/skills/my-skill/
├── SKILL.md              # Overview, how to use, core concepts
├── metadata.json         # Optional: version, org, references
├── README.md             # Optional: contribution guidelines
└── rules/
    ├── _sections.md      # Section definitions and priority order
    ├── _template.md      # Template for new rules
    ├── category-rule1.md
    ├── category-rule2.md
    └── other-rule3.md
```

### _sections.md Format

```markdown
---
title: Section Organization
---

## 1. Category Name (prefix)
**Impact:** CRITICAL
**Description:** What rules in this category cover.

## 2. Another Category (prefix2)
**Impact:** HIGH
**Description:** Another grouping of rules.
```

### Rule File Naming

Use prefix to group related rules:

```
trial-value-proposition.md
trial-cta-optimization.md
trial-social-proof.md
activation-onboarding-flow.md
activation-first-value.md
```

### Benefits

- **Maintainability** — Edit one rule without touching others
- **Discoverability** — Find rules by category prefix
- **Collaboration** — Multiple people can work on different rules
- **Prioritization** — Sort by impact level within sections

### Anti-Pattern

Don't create deeply nested directories. One level of `rules/` is enough.
