---
title: Use Case and Solution Pages
impact: MEDIUM-HIGH
tags: use-cases, solutions, verticals, personas, segments
---

## Use Case and Solution Pages

**Impact: MEDIUM-HIGH**

Use case pages answer "Is this for me?" by showing your product through the lens of specific personas, industries, or problems. They turn generic features into relevant solutions.

### Types of Solution Pages

| Type | URL Pattern | Example |
|------|-------------|---------|
| **Persona** | /solutions/[role] | /solutions/engineering-teams |
| **Industry/Vertical** | /solutions/[industry] | /solutions/healthcare |
| **Problem** | /solutions/[problem] | /solutions/remote-collaboration |
| **Use case** | /use-cases/[use-case] | /use-cases/sprint-planning |
| **Company size** | /solutions/[segment] | /solutions/enterprise |

### Solution Page Structure

```
┌────────────────────────────────────────────────────┐
│ 1. HERO                                            │
│    "[Product] for [Audience/Problem]"              │
│    Segment-specific value prop                     │
├────────────────────────────────────────────────────┤
│ 2. PROBLEM STATEMENT                               │
│    "You know the pain of..."                       │
│    Specific to this audience                       │
├────────────────────────────────────────────────────┤
│ 3. SOLUTION OVERVIEW                               │
│    How your product addresses their needs          │
│    Audience-relevant features highlighted          │
├────────────────────────────────────────────────────┤
│ 4. KEY CAPABILITIES                                │
│    Features framed for this audience               │
│    3-5 most relevant capabilities                  │
├────────────────────────────────────────────────────┤
│ 5. SOCIAL PROOF                                    │
│    Testimonials/cases from similar customers       │
│    Logos from the same segment                     │
├────────────────────────────────────────────────────┤
│ 6. WORKFLOW/USE CASE EXAMPLES                      │
│    "Here's how [Audience] uses [Product]"          │
│    Day-in-the-life scenarios                       │
├────────────────────────────────────────────────────┤
│ 7. COMPARISON TO STATUS QUO                        │
│    Before/after or vs spreadsheets/old way         │
├────────────────────────────────────────────────────┤
│ 8. CTA                                             │
│    Segment-specific call to action                 │
└────────────────────────────────────────────────────┘
```

### Solution Page Headlines

| Formula | Example | Best For |
|---------|---------|----------|
| **[Product] for [Audience]** | "Acme for Engineering Teams" | Persona pages |
| **[Outcome] for [Audience]** | "Faster deploys for DevOps teams" | Outcome-led |
| **[Problem] solved** | "Finally, sprint planning that works" | Problem-focused |
| **Built for [Audience]** | "Built for startups" | Audience validation |

### Good Solution Headlines

```
✓ "Project management built for engineering teams"
  → Clear audience + category positioning

✓ "Ship faster without the chaos"
  → Outcome + pain point addressed

✓ "Enterprise-grade security, startup-speed setup"
  → Addresses enterprise concerns with agility

✓ "Remote teams deserve better tools"
  → Validates the audience + implies solution
```

### Bad Solution Headlines

```
✗ "Solutions"
  → Says nothing

✗ "Our Enterprise Offering"
  → About you, not them

✗ "Acme for Everyone"
  → Defeats the purpose of segmentation

✗ "The Best Project Management Tool"
  → Generic, undifferentiated
```

### Writing Problem Statements

Speak to the specific pain points of this audience:

### Persona-Specific Problems

| Persona | Problem Statement |
|---------|-------------------|
| **Engineering** | "Your engineers are drowning in tickets, context-switching between tools, and losing hours to status updates that could be automated." |
| **Marketing** | "Campaign assets are scattered across Dropbox, Drive, and email threads. Feedback gets lost. Deadlines slip." |
| **Sales** | "Your CRM says one thing, your inbox says another, and your forecast is a guess at best." |
| **Operations** | "Process documentation lives in someone's head. Onboarding takes weeks. Mistakes repeat." |

### Industry-Specific Problems

| Industry | Problem Statement |
|----------|-------------------|
| **Healthcare** | "Patient coordination requires HIPAA compliance, but most tools weren't built for healthcare." |
| **Finance** | "Audit trails, compliance requirements, and data security aren't optional — they're table stakes." |
| **Startups** | "You need enterprise tools at startup prices, with zero implementation headaches." |

### Good Problem Section

```
✓ "Engineering teams spend 30% of their time on coordination, not code.

   You've tried Jira. You've tried spreadsheets. You've built internal tools.
   But sprint planning still takes hours. Standups still run over. And nobody
   knows what shipped last week without digging through Slack.

   Sound familiar?"
```

### Bad Problem Section

```
✗ "Companies today face many challenges in the modern business landscape.
   Collaboration is increasingly important, and teams need tools that
   help them work together effectively."
   → Generic, could apply to anyone
```

### Feature Framing by Audience

Same feature, different framing:

| Feature | For Engineering | For Marketing | For Ops |
|---------|-----------------|---------------|---------|
| **Automations** | "Automate ticket routing and status updates" | "Auto-assign tasks when campaigns launch" | "Trigger workflows on new hires" |
| **Dashboards** | "Track sprint velocity and deployment frequency" | "See campaign performance at a glance" | "Monitor SLA compliance" |
| **Integrations** | "Connect GitHub, Slack, and CI/CD" | "Sync with HubSpot and Google Analytics" | "Link to HRIS and payroll" |

### Good Capability Sections

```
✓ "For Engineering Teams"

   Sprint planning in minutes, not hours
   Drag-and-drop planning with automatic capacity calculation.
   Know exactly what fits in each sprint.

   Every code change, tracked
   GitHub integration links commits to tasks automatically.
   See the full context without leaving your workflow.

   Standups that run themselves
   Automated standup prompts and rollups.
   Get updates in Slack, keep everyone moving.
```

### Bad Capability Sections

```
✗ "Features"
   • Advanced dashboard capabilities
   • Real-time collaboration features
   • Powerful integration engine
   • Enterprise-grade security
   → Generic, not audience-specific
```

### Social Proof Strategy

| Audience | Proof Type | Example |
|----------|------------|---------|
| **Enterprise** | Logo bar + compliance certs | "Trusted by 500+ enterprises, SOC 2 certified" |
| **Startups** | Growth metrics + funded logos | "10,000+ startups including Y Combinator cos" |
| **Specific industry** | Industry logos + quote | "How Stripe's engineering team ships faster" |
| **Specific role** | Role-specific testimonial | Quote from VP Engineering |

### Good Social Proof

```
✓ "Engineering teams at Stripe, Figma, and Linear use Acme to ship faster"

   "We cut our sprint planning time by 60% and actually enjoy standups now."
   — Marcus Chen, VP Engineering, Linear

✓ "Trusted by 500+ healthcare organizations"
   [Logos: Cleveland Clinic, Kaiser, One Medical]
   HIPAA compliant • SOC 2 Type II • BAA available
```

### Use Case Example Format

```
✓ "A day in the life with Acme"

   8:30 AM — Morning standup
   Your team's updates are already collected. Just review and go.

   10:00 AM — Sprint planning
   Drag tasks, see capacity, assign work. Done in 15 minutes.

   2:00 PM — Code review
   PR merged, task auto-updated, Slack notified. No manual steps.

   5:00 PM — End of day
   Your dashboard shows what shipped. Ready for tomorrow's standup.
```

### Before/After Comparisons

| Element | Before (Status Quo) | After (Your Product) |
|---------|---------------------|----------------------|
| **Tool** | Spreadsheets, email | One unified platform |
| **Time** | Hours | Minutes |
| **Outcome** | Confusion, delays | Clarity, speed |
| **Feeling** | Frustration | Confidence |

### Good Before/After

```
✓ Before Acme:
   • Sprint planning takes 3+ hours
   • Status updates buried in Slack
   • Nobody knows what shipped

   After Acme:
   • Planning done in 30 minutes
   • Updates automatic and visible
   • Real-time shipping dashboard
```

### Segment-Specific CTAs

| Audience | Primary CTA | Secondary CTA |
|----------|-------------|---------------|
| **Enterprise** | "Talk to sales" | "See security overview" |
| **Startup** | "Start free" | "See startup pricing" |
| **Technical** | "Read the docs" | "Try the API" |
| **Non-technical** | "See it in action" | "Book a demo" |

### Solution Page Checklist

- [ ] Headline speaks directly to the audience
- [ ] Problem statement is audience-specific
- [ ] Features are framed for this audience
- [ ] Social proof from similar customers
- [ ] Use cases relevant to their workflow
- [ ] Before/after shows clear improvement
- [ ] CTA matches audience expectations
- [ ] Cross-links to relevant case studies
- [ ] Page can stand alone (visitors may land here first)

### SEO Optimization

| Element | Best Practice |
|---------|---------------|
| **Title** | "[Product] for [Audience] | [Outcome]" |
| **Meta** | "[Product] helps [Audience] [outcome]. [Specific benefit]..." |
| **H1** | "[Product] for [Audience]" |
| **URL** | /solutions/[audience-slug] |
| **Content** | Naturally include role/industry terms |

### Anti-Patterns

- **Copy-paste pages** — Each solution page must be genuinely different
- **Generic features** — Frame everything for the specific audience
- **Wrong social proof** — Enterprise logos on startup page fails
- **No problem validation** — Show you understand their pain
- **One-size-fits-all CTAs** — Enterprises want to "talk to sales"
- **Missing specificity** — "Marketing teams" is too broad
- **Ignoring objections** — Address segment-specific concerns
- **No workflow examples** — Show the product in their context
- **Jargon mismatch** — Use their vocabulary, not yours
- **Orphaned pages** — Link from navigation and other pages
