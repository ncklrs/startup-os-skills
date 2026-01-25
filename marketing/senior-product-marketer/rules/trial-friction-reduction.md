---
title: Signup Friction Reduction
impact: CRITICAL
tags: trial, signup, forms
---

## Signup Friction Reduction

**Impact: CRITICAL**

Every form field costs you 10-15% of signups. Be ruthless.

### The Hierarchy

1. **Zero-friction:** Social login / SSO only
2. **Low-friction:** Email + magic link
3. **Medium-friction:** Email + password
4. **High-friction:** Email + password + verification + profile
5. **Death:** Company name + role + phone + CAPTCHA + verification

### What to Remove

| Field | Remove? | Why |
|-------|---------|-----|
| First name | Yes | Infer from email or ask later |
| Last name | Yes | Not needed for trial |
| Company name | Yes | Auto-detect or ask post-activation |
| Phone number | Yes | Unless sales-led motion |
| Password confirmation | Yes | Use visibility toggle instead |
| CAPTCHA | Maybe | Only if abuse is proven problem |

### Progressive Profiling

Ask for additional info AFTER the user has experienced value:

```
✓ Signup: Email only
✓ First value: "What's your role?" (improves recommendations)
✓ Day 3: "How big is your team?" (qualifies for sales)
✓ Upgrade: Full billing details
```

### Anti-Pattern

"We need their phone for sales follow-up" — If they don't activate, you have nothing to follow up on.
