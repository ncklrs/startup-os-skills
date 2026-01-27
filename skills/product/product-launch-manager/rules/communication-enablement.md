---
title: Internal Enablement for Launches
impact: HIGH
tags: communication, enablement, sales, support, training
---

## Internal Enablement for Launches

**Impact: HIGH**

Your internal teams are your first launch audience. If Sales can't explain it and Support can't troubleshoot it, you've already failed.

### Enablement Timeline

| Milestone | Sales | Support | CS | Marketing |
|-----------|-------|---------|-----|-----------|
| T-4 weeks | Feature preview | Feature preview | Feature preview | Deep dive |
| T-3 weeks | Value prop training | Documentation review | Use case review | Content creation |
| T-2 weeks | Objection handling | Troubleshooting training | Talk track practice | Final content |
| T-1 week | Battlecard delivery | FAQ finalized | Customer prep | Launch prep |
| Launch | Ready to sell | Ready to support | Ready to expand | Go live |

### Sales Enablement Package

**Required Materials:**

| Asset | Purpose | Owner | Timing |
|-------|---------|-------|--------|
| One-pager | Quick reference | PMM | T-2 weeks |
| Battlecard | Competitive positioning | PMM | T-2 weeks |
| Talk track | Discovery questions | PMM + Sales | T-2 weeks |
| Demo script | Standardized demo | PMM | T-1 week |
| Objection handling | Common pushback | PMM + Sales | T-1 week |
| Pricing guide | If applicable | Product | T-2 weeks |
| Customer stories | Social proof | PMM | T-1 week |

### Good Example: Sales One-Pager

```markdown
# Enterprise SSO - Sales One-Pager

## What It Is
Single Sign-On integration supporting SAML 2.0, OIDC, and
SCIM provisioning for enterprise identity providers.

## Who It's For
- Enterprise companies (500+ employees)
- Security-conscious organizations
- Companies with existing IdP (Okta, Azure AD, etc.)

## Key Value Props
1. **Security compliance** - Meet SOC 2, HIPAA requirements
2. **IT efficiency** - Automated user provisioning/deprovisioning
3. **User experience** - One-click login, no password fatigue

## Discovery Questions
- "How do you currently manage user access across tools?"
- "What's your offboarding process when employees leave?"
- "Are you facing any compliance requirements around access control?"

## Objection Handling
| Objection | Response |
|-----------|----------|
| "Too expensive" | SSO reduces password reset tickets by 40% |
| "We use [competitor]" | We support same IdPs + faster setup |
| "Not a priority" | Security breaches cost avg $4.2M |

## Pricing
- Included in Enterprise plan ($X/user/month)
- Available as add-on for Business plan (+$Y/user/month)

## Demo Environment
- sandbox-sso.company.com
- Credentials: demo@company.com / [in 1Password]
```

### Bad Example: No Enablement

```markdown
## What Happened: Widget 2.0 Launch

**Sales Team Experience:**
- Found out about launch from customer LinkedIn post
- No training provided
- Had to read blog post to understand feature
- Demo environment not set up
- First customer call: "I don't know, let me get back to you"

**Support Team Experience:**
- Received first ticket before documentation existed
- No troubleshooting guide
- Had to reverse-engineer feature from code
- 2-hour average response time (normally 30 min)

**Result:**
- Lost 3 enterprise deals in first week
- Support CSAT dropped 20 points
- Team morale damaged
- Customer trust eroded
```

### Support Enablement Package

**Required Materials:**

| Asset | Purpose | Owner | Timing |
|-------|---------|-------|--------|
| Feature documentation | Reference | Technical Writer | T-2 weeks |
| FAQ document | Quick answers | Product + Support | T-1 week |
| Troubleshooting guide | Issue resolution | Engineering + Support | T-1 week |
| Known issues list | Transparency | Engineering | Launch day |
| Escalation matrix | When to escalate | Support Lead | T-1 week |
| Canned responses | Efficiency | Support Lead | T-1 week |

### Good Example: Support Troubleshooting Guide

```markdown
# SSO Troubleshooting Guide

## Common Issues & Resolutions

### Issue: SAML assertion error
**Symptoms:** User sees "Invalid SAML response" on login
**Likely Causes:**
1. Clock skew between IdP and our servers
2. Incorrect assertion consumer URL
3. Certificate mismatch

**Resolution Steps:**
1. Check IdP configuration matches our setup guide
2. Verify assertion URL is `https://app.company.com/sso/callback`
3. Compare certificate thumbprint in Admin > SSO settings
4. If persists, collect SAML trace (instructions below)

**Escalation:** If unresolved after 3 attempts, escalate to
Tier 2 with SAML trace attached.

### Issue: SCIM sync failing
**Symptoms:** Users not provisioning/deprovisioning
**Likely Causes:**
1. SCIM token expired
2. Rate limiting
3. User attribute mapping mismatch

**Resolution Steps:**
1. Verify SCIM token in Admin > Integrations
2. Check our status page for rate limit issues
3. Review attribute mapping in IdP
4. Run manual sync from Admin panel

**Escalation:** If sync queue > 1000 users, escalate to
Engineering with org ID.
```

### Customer Success Enablement

| Asset | Purpose | Owner | Timing |
|-------|---------|-------|--------|
| Expansion talk track | Upsell opportunity | CS + PMM | T-2 weeks |
| Customer announcement | Inform existing customers | CS | Launch day |
| Implementation guide | Adoption support | CS | T-1 week |
| Health score impact | How feature affects metrics | Product | T-2 weeks |

### Enablement Delivery Methods

| Method | Best For | Timing | Duration |
|--------|----------|--------|----------|
| Live training | Major features, Q&A | T-2 weeks | 30-60 min |
| Recorded video | Reference, async teams | T-2 weeks | 10-15 min |
| Documentation | Detailed reference | T-2 weeks | Self-paced |
| Slack announcement | Awareness, quick updates | Launch day | 5 min read |
| Office hours | Questions, edge cases | T-1 week | 30 min |

### Enablement Certification

For Tier 1/2 launches, consider requiring certification:

```
Sales Certification Checklist
─────────────────────────────
□ Completed training video (15 min)
□ Passed quiz (80% minimum)
□ Delivered practice demo to manager
□ Reviewed battlecard
□ Shadowed one customer call

Certification valid until: [Date]
```

### Enablement Feedback Loop

```
Week 1 Post-Launch:
├── "What questions are customers asking?"
├── "What objections are you hearing?"
├── "What's missing from materials?"
└── "What's confusing in documentation?"

Action: Update materials based on feedback
```

### Anti-Patterns

- **Launch day enablement** — Training the day of launch
- **Email-only enablement** — No one reads long emails
- **No certification** — Assuming everyone will self-enable
- **One-and-done** — No iteration based on feedback
- **PMM creates alone** — Sales and Support not involved in creation
- **Different versions** — Sales and Support telling different stories
- **No demo environment** — "Just describe it to customers"
- **Technical-only docs** — No business context for Sales
