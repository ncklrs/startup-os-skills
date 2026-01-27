---
title: Edge Cases and Error Handling
impact: HIGH
tags: edge-cases, errors, error-handling, failure-modes, resilience
---

## Edge Cases and Error Handling

**Impact: HIGH**

Edge cases and error handling separate polished products from frustrating ones. Documenting failure modes upfront prevents surprises in production and reduces debugging time.

### Why Document Edge Cases

1. **Prevent production surprises** — Known unknowns are better than unknown unknowns
2. **Enable QA coverage** — Testers need to know what to test
3. **Guide error messages** — Users need helpful feedback
4. **Inform monitoring** — Know what to alert on
5. **Reduce tech debt** — Handle cases properly the first time

### Edge Case Categories

| Category | Description | Example |
|----------|-------------|---------|
| **Boundary** | Min/max limits | 0 items, max characters |
| **Timing** | Race conditions, expiration | Concurrent edits, expired session |
| **State** | Invalid transitions | Cancel paid order, edit deleted item |
| **Data** | Missing, corrupt, unexpected | Null values, unicode, large files |
| **External** | Third-party failures | API down, timeout, rate limited |
| **Permission** | Access edge cases | Deleted user, transferred ownership |
| **Network** | Connectivity issues | Offline, slow connection, timeout |
| **Concurrency** | Simultaneous operations | Double submit, parallel updates |

### Edge Case Documentation Template

```markdown
## Edge Case: [Name]

**Category:** [Boundary/Timing/State/Data/External/Permission/Network/Concurrency]
**Likelihood:** [Common/Occasional/Rare]
**Impact:** [Critical/High/Medium/Low]

**Scenario:**
[Describe the specific situation]

**Current Behavior:**
[What happens now, if anything]

**Desired Behavior:**
[What should happen]

**User Message:**
[Exact error message to display]

**Recovery Action:**
[What user can do to resolve]

**Technical Notes:**
[Implementation considerations]
```

### Comprehensive Edge Case Example

**Feature: File Upload**

```markdown
## Edge Cases: File Upload

### Boundary Cases

| Case | Limit | Behavior | User Message |
|------|-------|----------|--------------|
| File too large | >100MB | Reject before upload | "File exceeds 100MB limit. Try compressing or splitting." |
| File name too long | >255 chars | Truncate with hash | N/A (silent truncation) |
| Zero-byte file | 0 bytes | Allow (may be intentional) | N/A |
| Filename with special chars | Unicode, spaces | Sanitize on backend | N/A (accept as-is, sanitize storage name) |

### Timing Cases

| Case | Trigger | Behavior | User Message |
|------|---------|----------|--------------|
| Upload timeout | >5 min upload | Retry with resume | "Upload interrupted. Resuming..." |
| Session expires mid-upload | Auth token expires | Complete upload, fail on save | "Session expired. Please log in and retry." |
| User navigates away | Browser tab closed | Cancel upload | Confirmation: "Upload in progress. Leave anyway?" |

### State Cases

| Case | Trigger | Behavior | User Message |
|------|---------|----------|--------------|
| Folder deleted during upload | Target deleted | Create folder or reject | "Destination folder no longer exists. Select new location." |
| Storage quota exceeded | Plan limit | Reject upload | "Storage limit reached. Upgrade plan or delete files." |
| Duplicate filename | Same name exists | Prompt for resolution | "File already exists. Replace, rename, or cancel?" |

### Data Cases

| Case | Trigger | Behavior | User Message |
|------|---------|----------|--------------|
| Corrupt file | Invalid header | Attempt upload, warn on view | "File may be corrupt. Upload anyway?" |
| Unsupported format | Blocked extension | Reject | "File type .exe not allowed. Supported: pdf, doc, jpg..." |
| Malware detected | Virus scan positive | Reject, log security event | "File flagged as potentially harmful. Contact support." |
| Image with EXIF data | Privacy concern | Strip EXIF on upload | N/A (silent strip) |

### External Dependency Cases

| Case | Trigger | Behavior | User Message |
|------|---------|----------|--------------|
| S3 unavailable | AWS outage | Queue for retry | "Upload processing. You'll be notified when complete." |
| Virus scanner timeout | Scan service slow | Allow with async scan | "File uploaded. Security scan in progress." |
| CDN propagation delay | New file not available | Show from origin | N/A (transparent fallback) |

### Network Cases

| Case | Trigger | Behavior | User Message |
|------|---------|----------|--------------|
| Connection lost | Network drop | Pause, auto-retry | "Connection lost. Will resume when online." |
| Slow upload (<100kb/s) | Poor connection | Show warning, continue | "Slow connection detected. Upload may take longer." |
| Packet loss | Unstable network | Retry chunks | N/A (transparent retry) |

### Concurrency Cases

| Case | Trigger | Behavior | User Message |
|------|---------|----------|--------------|
| Double click upload | User impatience | Debounce, single upload | N/A (ignore duplicate click) |
| Same file from two tabs | Multiple sessions | Both succeed, detect duplicate | "This file was uploaded in another tab." |
| Replace file during download | Concurrent access | Version old file | N/A (serve consistent version) |
```

### Error Taxonomy

**Organize errors by recoverability:**

| Type | User Can Fix? | Response Strategy |
|------|--------------|-------------------|
| **Validation** | Yes | Inline errors, clear instructions |
| **Authentication** | Yes | Redirect to login |
| **Authorization** | Sometimes | Explain permission, link to request access |
| **Not Found** | Sometimes | Search suggestions, "did you mean" |
| **Conflict** | Yes | Show current state, resolution options |
| **Rate Limit** | Wait | Show when to retry |
| **Server Error** | No | Apologize, suggest retry, link to status page |
| **Maintenance** | No | Estimated return time |

### Error Message Guidelines

**Structure:**
```
[What happened] + [Why it matters] + [What to do next]
```

**Good Error Messages:**

| Situation | Good Message |
|-----------|--------------|
| Invalid email | "Please enter a valid email address (e.g., name@company.com)" |
| Payment failed | "Payment declined by your bank. Try another card or contact your bank." |
| Permission denied | "You need Editor access to modify this document. Request access from Sarah M." |
| Rate limited | "You've made too many requests. Please wait 5 minutes before trying again." |
| Server error | "Something went wrong on our end. We've been notified. Try again in a few minutes." |

**Bad Error Messages:**

| Bad | Why | Better |
|-----|-----|--------|
| "Error" | No information | "Unable to save changes" |
| "Error 403" | Technical jargon | "You don't have permission" |
| "Invalid input" | Vague | "Username must be 3-20 characters" |
| "Request failed" | No next step | "Request failed. Check connection and retry." |
| "null reference exception" | Exposes internals | "Something went wrong. Try again." |

### Error Handling Matrix

| Error Type | Log Level | Alert? | User Feedback | Auto Retry? |
|------------|-----------|--------|---------------|-------------|
| Validation | Debug | No | Inline error | No |
| Auth failure | Info | No | Modal/redirect | No |
| Not found | Warn | If pattern | Empty state | No |
| Rate limit | Warn | If excessive | Toast | Yes (delayed) |
| Timeout | Warn | If SLA breach | Toast | Yes (3x) |
| DB error | Error | Yes | Generic error | Yes (2x) |
| Critical | Fatal | Yes (PagerDuty) | Maintenance page | No |

### Documenting Failure Modes

**For each integration/dependency:**

```markdown
## Dependency: Stripe Payment API

### Failure Modes

| Failure | Detection | Impact | Mitigation |
|---------|-----------|--------|------------|
| API timeout (>10s) | HTTP timeout | Payment stuck | Retry 3x, then queue |
| Invalid API key | 401 response | All payments fail | Alert, manual fix |
| Card declined | Decline code | Single payment fails | Show user message |
| Rate limited | 429 response | Slowdown | Exponential backoff |
| Webhook missed | No event received | Data out of sync | Polling reconciliation |
| API deprecation | Warning header | Future breakage | Log, plan upgrade |

### Fallback Behavior

- Primary: Stripe API direct call
- Retry: 3 attempts with exponential backoff (1s, 2s, 4s)
- Queue: If all retries fail, queue for background processing
- Alert: If queue depth > 100 or age > 1 hour
- Manual: Admin can force-retry or refund

### Recovery Procedures

1. Check Stripe status page
2. Verify API key validity
3. Check rate limit headers
4. Review recent code changes
5. Escalate to Stripe support if needed
```

### Edge Case Discovery Checklist

When specifying a feature, ask:

```
Inputs
├── □ What if input is empty/null?
├── □ What if input is at minimum value?
├── □ What if input is at maximum value?
├── □ What if input exceeds maximum?
├── □ What if input has unexpected characters?
├── □ What if input has malicious content?
└── □ What if input is in wrong format?

Timing
├── □ What if action is very slow?
├── □ What if action times out?
├── □ What if action is interrupted?
├── □ What if session expires during action?
└── □ What if two users act simultaneously?

State
├── □ What if resource doesn't exist?
├── □ What if resource was just deleted?
├── □ What if resource is locked/in use?
├── □ What if user loses permission during action?
└── □ What if related resources change?

External
├── □ What if third-party service is down?
├── □ What if third-party returns unexpected data?
├── □ What if network is unavailable?
└── □ What if response is slow?
```

### Anti-Patterns

- **Happy path only** — Only documenting success scenarios
- **Generic errors** — "Something went wrong" for everything
- **Silent failures** — Errors swallowed without feedback
- **Technical messages** — Showing stack traces to users
- **Unhandled states** — Loading forever, no empty states
- **Inconsistent handling** — Same error, different treatment
- **No recovery path** — Errors without guidance on fixing
- **Over-alerting** — Every error pages on-call
- **Under-logging** — No audit trail when things go wrong
- **Blame the user** — "Invalid input" without explaining what's valid
