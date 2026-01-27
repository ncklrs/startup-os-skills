---
title: Domain Expert Skill Pattern
impact: MEDIUM
tags: patterns, skill-types
---

## Domain Expert Skill Pattern

**Impact: MEDIUM**

For encoding specialized knowledge in a specific field.

### When to Use

- Subject matter expertise (security, performance, marketing)
- Industry knowledge (healthcare, fintech, e-commerce)
- Role-based guidance (senior engineer, product manager)

### Structure

```
skills/senior-security-engineer/
├── SKILL.md           # Core principles, frameworks, mental models
└── rules/             # Optional: specific guidelines by area
    ├── auth-*.md
    ├── crypto-*.md
    └── infra-*.md
```

### SKILL.md Content

```markdown
---
name: senior-security-engineer
description: Security engineering expertise for application security,
             infrastructure hardening, and secure development practices.
             Use when reviewing code for vulnerabilities, designing
             auth systems, or implementing security controls.
---

# Senior Security Engineer

## Core Principles

1. Defense in depth
2. Least privilege
3. Fail secure

## Mental Models

### Threat Modeling
[How to think about threats]

### Attack Surface Analysis
[How to identify exposure]

## Key Frameworks

- OWASP Top 10
- CIS Controls
- Zero Trust Architecture
```

### What Makes It Work

- **Principles first** — Start with mental models, not rules
- **Frameworks** — Reference established knowledge
- **Judgment calls** — Explain trade-offs, not just answers

### Anti-Pattern

Don't just list facts. Encode *how an expert thinks* about problems.
