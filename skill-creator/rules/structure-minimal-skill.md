---
title: Minimal Skill Structure
impact: CRITICAL
tags: structure, getting-started
---

## Minimal Skill Structure

**Impact: CRITICAL**

Start simple. A skill only needs one file: `SKILL.md` with frontmatter.

### Required Structure

```
~/.claude/skills/
└── my-skill/
    └── SKILL.md
```

### Minimal SKILL.md

```yaml
---
name: my-skill
description: Brief description with trigger phrases. Use when X, Y, or Z.
---

# My Skill

Content goes here. Can be guidelines, knowledge, procedures, or constraints.
```

### When to Use Minimal

- Skill has < 10 guidelines
- Content fits in one readable file
- No need for versioning or categorization

### When to Expand

Upgrade to rules directory when:
- Content exceeds 500 lines
- Guidelines fall into distinct categories
- Multiple contributors need to edit different sections
- You want impact-level prioritization

### Anti-Pattern

Don't create `rules/` directory with only 2-3 files. Keep it simple until complexity is needed.
