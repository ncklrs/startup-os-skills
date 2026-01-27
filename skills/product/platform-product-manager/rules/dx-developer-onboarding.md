---
title: Developer Onboarding
impact: CRITICAL
tags: dx, onboarding, activation, time-to-value
---

## Developer Onboarding

**Impact: CRITICAL**

Time-to-first-API-call is your most important activation metric. Every minute of friction loses developers.

### The Developer Onboarding Funnel

```
SIGNUP                          100% ────────────────────────
    │
    ▼ (friction: forms, email verify)
GET API KEY                      70% ─────────────────
    │
    ▼ (friction: complexity, confusion)
FIRST API CALL                   40% ───────────
    │
    ▼ (friction: setup, environment)
USE CASE COMPLETED               20% ─────
    │
    ▼ (friction: edge cases, support)
ACTIVE DEVELOPER                 10% ──
```

**Goal: Maximize conversion at each step.**

### Time-to-First-Call Benchmarks

| Rating | Time | Example Actions |
|--------|------|-----------------|
| **Excellent** | < 5 minutes | Stripe, Twilio |
| **Good** | 5-15 minutes | Most modern APIs |
| **Acceptable** | 15-30 minutes | Enterprise APIs |
| **Poor** | 30-60 minutes | Needs improvement |
| **Failing** | > 60 minutes | Major DX investment needed |

### Onboarding Flow Design

**Good onboarding flow:**

```
1. SIGNUP (30 seconds)
   - OAuth/SSO option
   - Minimal fields (email + password)
   - No email verification for sandbox

2. API KEY (1 minute)
   - Auto-generated on signup
   - Visible immediately on dashboard
   - Copy button with feedback

3. QUICKSTART (5 minutes)
   - Language selector
   - Copy-paste code samples
   - Test endpoint (sandbox)

4. FIRST SUCCESS (10 minutes)
   - Guided tutorial
   - Real use case completed
   - Clear next steps
```

**Bad onboarding flow:**

```
1. Long signup form (5+ fields)
2. Email verification required
3. Company approval/waitlist
4. Dashboard tour that can't be skipped
5. API key hidden in settings
6. No code samples
7. Documentation only (no quickstart)
```

### Quickstart Page Anatomy

**Essential elements:**

```markdown
# Quickstart

## 1. Install the SDK

[Language tabs: curl | Python | Node | Ruby | Go | Java]

```bash
pip install example-sdk
```

## 2. Get Your API Key

Your API key: `sk_test_4eC39Hq...` [Copy]

## 3. Make Your First Request

```python
import example

client = example.Client("sk_test_4eC39HqL...")
result = client.users.create(email="test@example.com")
print(result.id)  # usr_123abc
```

## 4. Verify It Worked

Check your [Dashboard →] to see the user you just created.

## Next Steps
- [Complete guide →]
- [API reference →]
- [Code examples →]
```

### Interactive Sandbox Requirements

| Feature | Priority | Impact |
|---------|----------|--------|
| **No signup required** | Critical | Removes biggest friction |
| **Pre-filled examples** | Critical | Instant start |
| **Real API responses** | High | Builds confidence |
| **Multiple languages** | High | Serves all developers |
| **Save/share code** | Medium | Team collaboration |
| **Error explanations** | Medium | Self-service debugging |

### Onboarding Checklist Pattern

**Dashboard progress indicator:**

```
Getting Started                    2 of 4 complete
─────────────────────────────────────────────────

[✓] Create account
[✓] Get API key
[ ] Make first API call           [Start →]
[ ] Set up webhooks               [Learn more →]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### First-Run Experience Best Practices

**Do:**
- Show API key immediately after signup
- Provide one-click copy for keys and code
- Default to test/sandbox mode
- Include inline code validation
- Show success confirmation
- Suggest logical next steps

**Don't:**
- Require payment info for trial
- Hide API keys in nested menus
- Force dashboard tour
- Start in production mode
- Leave developers wondering "did it work?"

### Language Prioritization

**Prioritize SDK/docs by adoption:**

| Priority | Languages | Reasoning |
|----------|-----------|-----------|
| **Tier 1** | Python, JavaScript/Node, curl | Highest adoption |
| **Tier 2** | Go, Ruby, Java | Strong in specific verticals |
| **Tier 3** | PHP, C#/.NET | Enterprise/legacy |
| **Tier 4** | Swift, Kotlin | Mobile-specific |

### Measuring Onboarding Success

**Key metrics:**

| Metric | Formula | Target |
|--------|---------|--------|
| **Time to API key** | Signup → key generated | < 2 min |
| **Time to first call** | Signup → first API request | < 15 min |
| **Activation rate** | First call / Signups | > 50% |
| **Day 1 retention** | Active day 2 / Signups | > 30% |
| **Time to value** | Signup → use case complete | < 1 hour |

### Onboarding Error Handling

**Good error experience:**

```json
{
  "error": {
    "code": "invalid_api_key",
    "message": "The API key provided is invalid",
    "suggestion": "Make sure you're using your API key from the dashboard, not the publishable key",
    "doc_url": "https://docs.example.com/authentication"
  }
}
```

**Inline suggestions:**

```
Error: 401 Unauthorized

Looks like your API key might be incorrect. Here's how to fix it:

1. Go to Dashboard → API Keys
2. Copy your Secret Key (starts with sk_)
3. Make sure you're using the test key for sandbox

[Get your API key →]
```

### Anti-Patterns

- **Sales wall** — Requiring demo/call before API access
- **Key scavenger hunt** — API key buried in settings
- **Docs-only quickstart** — No interactive elements
- **Production-first** — Starting developers in production mode
- **No curl examples** — Forcing SDK for simple tests
- **One-size-fits-all** — Same onboarding for all use cases
- **Abandoned onboarding** — No follow-up for stuck developers
- **Success silence** — No confirmation when things work
