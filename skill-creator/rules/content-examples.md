---
title: Good and Bad Examples
impact: HIGH
tags: content, examples, clarity
---

## Good and Bad Examples

**Impact: HIGH**

Every guideline should show what to do AND what not to do.

### Example Format

```markdown
### Bad Example

\`\`\`typescript
// Explain why this is wrong
const bad = doThingWrong();
\`\`\`

### Good Example

\`\`\`typescript
// Explain why this is right
const good = doThingRight();
\`\`\`
```

### Why Both Matter

- **Good examples** show the target state
- **Bad examples** help recognize anti-patterns
- Together they create clear boundaries

### Real-World Examples Are Best

```markdown
### Bad — Generic

Don't write bad code.

### Good — Specific

**Bad:** Nesting callbacks 5 levels deep
\`\`\`javascript
getData(function(a) {
  getMore(a, function(b) {
    andMore(b, function(c) {
      // callback hell
    });
  });
});
\`\`\`

**Good:** Using async/await for readability
\`\`\`javascript
const a = await getData();
const b = await getMore(a);
const c = await andMore(b);
\`\`\`
```

### Checklist for Examples

- [ ] Shows realistic code/content, not toy examples
- [ ] Explains *why* it's good or bad
- [ ] Can be copy-pasted and adapted
- [ ] Matches the skill's domain and language

### Anti-Pattern

Guidelines without examples are just opinions. Show, don't just tell.
