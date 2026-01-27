---
title: Trigger Phrases for Discovery
impact: HIGH
tags: discovery, description, invocation
---

## Trigger Phrases for Discovery

**Impact: HIGH**

Claude uses the `description` field to decide when to suggest a skill. Include phrases users actually say.

### Trigger Phrase Patterns

| Pattern | Example |
|---------|---------|
| "Use when" | Use when writing landing pages |
| "Use for" | Use for React performance optimization |
| "Asked to" | When asked to "review my UI" |
| Keywords | accessibility, conversion, onboarding |
| Actions | writing, reviewing, building, optimizing |

### Good Description Example

```yaml
description: >
  Expert product marketing guidance for SaaS growth - trial acquisition,
  user activation to first value, and freemium-to-paid conversion.
  Use when writing landing pages, onboarding flows, email sequences,
  pricing pages, upgrade prompts, or any growth/conversion copy.
```

This triggers on:
- "help me write a landing page"
- "optimize our onboarding flow"
- "improve conversion rates"
- "write upgrade prompts"

### Bad Description Example

```yaml
description: Marketing skill for products.
```

This triggers on almost nothing specific.

### Testing Triggers

After creating a skill, test with prompts like:
- "Help me [action] [thing]"
- "I need to [task]"
- "[keyword] best practices"

### Anti-Pattern

Don't include every possible keyword. Focus on the 5-10 most common ways users would ask for this help.
