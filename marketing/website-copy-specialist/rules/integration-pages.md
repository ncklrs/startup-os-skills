---
title: Integration Pages
impact: MEDIUM-HIGH
tags: integrations, ecosystem, connectors, apps
---

## Integration Pages

**Impact: MEDIUM-HIGH**

Integration pages capture high-intent searches like "[Your Product] + [Tool]" and prove your product fits their existing workflow. They're SEO goldmines and trust builders.

### Integration Page Types

| Type | URL Pattern | Purpose |
|------|-------------|---------|
| **Hub page** | /integrations | Overview of all integrations |
| **Category page** | /integrations/[category] | Group by type (CRM, DevOps) |
| **Single integration** | /integrations/[tool] | Deep dive on one tool |
| **Native feature** | /features/[tool]-integration | Built-in vs add-on |

### Integration Hub Structure

```
┌────────────────────────────────────────────────────┐
│ 1. HERO                                            │
│    "Connect [Product] to your favorite tools"      │
│    Number of integrations + search bar             │
├────────────────────────────────────────────────────┤
│ 2. FEATURED INTEGRATIONS                           │
│    Most popular or requested (6-12)                │
│    Logos with quick descriptions                   │
├────────────────────────────────────────────────────┤
│ 3. CATEGORY SECTIONS                               │
│    Grouped by use case or tool type                │
│    Expandable or filterable list                   │
├────────────────────────────────────────────────────┤
│ 4. API/BUILD YOUR OWN                              │
│    Developer resources for custom integrations     │
├────────────────────────────────────────────────────┤
│ 5. REQUEST INTEGRATION                             │
│    Form or link to request new integrations        │
├────────────────────────────────────────────────────┤
│ 6. CTA                                             │
│    "Start free and connect your tools"             │
└────────────────────────────────────────────────────┘
```

### Single Integration Page Structure

```
┌────────────────────────────────────────────────────┐
│ 1. HERO                                            │
│    "[Product] + [Tool]" with both logos            │
│    One-line value prop                             │
├────────────────────────────────────────────────────┤
│ 2. KEY BENEFITS                                    │
│    What this integration enables (3-5)             │
│    Specific to this combination                    │
├────────────────────────────────────────────────────┤
│ 3. HOW IT WORKS                                    │
│    Setup process (usually 3 steps)                 │
│    What syncs, triggers, actions                   │
├────────────────────────────────────────────────────┤
│ 4. USE CASES                                       │
│    2-3 specific scenarios                          │
│    "Perfect for teams who..."                      │
├────────────────────────────────────────────────────┤
│ 5. TECHNICAL DETAILS                               │
│    Data sync, permissions, security                │
│    For evaluators doing due diligence              │
├────────────────────────────────────────────────────┤
│ 6. TESTIMONIAL                                     │
│    Customer using this specific integration        │
├────────────────────────────────────────────────────┤
│ 7. RELATED INTEGRATIONS                            │
│    Other tools in same category                    │
├────────────────────────────────────────────────────┤
│ 8. CTA                                             │
│    "Connect [Tool] now" or "Start free trial"      │
└────────────────────────────────────────────────────┘
```

### Integration Page Headlines

| Formula | Example | Best For |
|---------|---------|----------|
| **[Product] + [Tool]** | "Acme + Slack" | SEO, clarity |
| **Connect [Product] to [Tool]** | "Connect Acme to Salesforce" | Action-oriented |
| **[Product] [Tool] Integration** | "Acme Slack Integration" | Search-optimized |
| **[Benefit] with [Tool]** | "Get notified in Slack" | Benefit-led |

### Good Integration Headlines

```
✓ "Acme + GitHub: Code changes, automatically tracked"
  → Both products + specific value

✓ "Bring Acme into Slack"
  → Action-oriented, tool-first

✓ "Sync your CRM with Acme"
  → Category approach for hub pages

✓ "Two-way sync with Salesforce"
  → Technical specificity
```

### Bad Integration Headlines

```
✗ "Integration"
  → Zero information

✗ "Our Slack Solution"
  → Vague, generic

✗ "Powerful Third-Party Connectivity"
  → Jargon, no specificity

✗ "Integrations Page"
  → Wasted headline opportunity
```

### Writing Integration Benefits

Focus on what becomes possible, not what's connected:

| Integration | Don't Say | Say This |
|-------------|-----------|----------|
| **Slack** | "Sends data to Slack" | "Get alerts where you already work" |
| **Salesforce** | "Syncs with CRM" | "See customer context without switching tabs" |
| **GitHub** | "Connects to repositories" | "Link code changes to project tasks" |
| **Zapier** | "Works with Zapier" | "Connect to 5,000+ apps without code" |

### Good Integration Benefits

```
✓ "Acme + Slack"

   • Get notified instantly
     New comments, assignments, and updates appear in your Slack
     channels automatically.

   • Reply without leaving Slack
     Respond to comments, update statuses, and assign tasks
     directly from Slack.

   • Keep everyone in the loop
     Weekly digests and real-time alerts keep your team aligned.
```

### Bad Integration Benefits

```
✗ "Acme + Slack"

   • Slack integration
   • Real-time notifications
   • Data synchronization
   • Bi-directional communication
   → Feature list without user value
```

### How It Works Section

Keep it to 3 steps maximum:

```
✓ "How to connect Acme and Slack"

   1. Click "Connect to Slack" in your Acme settings
      Authorize Acme to access your Slack workspace.

   2. Choose your channels
      Select which Slack channels receive Acme updates.

   3. You're connected
      Updates flow automatically. Customize in settings anytime.

   Setup time: Under 2 minutes
   Permissions required: Read/write to selected channels
```

### Technical Details Section

| Element | What to Include |
|---------|-----------------|
| **Sync frequency** | Real-time, hourly, daily |
| **Data flow** | One-way or bi-directional |
| **What syncs** | Specific objects/data types |
| **Permissions** | What access is needed |
| **Security** | How data is protected |
| **Limitations** | Any known constraints |

### Good Technical Details

```
✓ "Technical Details"

   Sync type: Real-time, bi-directional
   Data synced: Projects, tasks, comments, attachments
   Permissions: Read/write access to selected channels
   Security: OAuth 2.0, data encrypted in transit
   Rate limits: 10,000 API calls per hour
   Requirements: Slack Business plan or higher
```

### Use Cases for Integration Pages

```
✓ "Perfect for teams who..."

   • Track GitHub issues alongside product tasks
   • Want developers notified without leaving their IDE
   • Need deployment events linked to project milestones

✓ "Common workflows"

   • When a PR is merged → Task marked complete
   • When a bug is filed → Slack alert + task created
   • When a release ships → Stakeholders notified
```

### Integration Page CTAs

| Context | Primary CTA | Secondary CTA |
|---------|-------------|---------------|
| **Has account** | "Connect [Tool]" | "View setup guide" |
| **No account** | "Start free trial" | "See how it works" |
| **Enterprise tool** | "Talk to sales" | "Read documentation" |

### Good Integration CTAs

```
✓ "Already have an Acme account?"
   [Connect Slack now]

✓ "New to Acme?"
   [Start free trial — connect Slack in minutes]

✓ For enterprise integrations:
   [Contact sales for Salesforce Enterprise setup]
```

### Category Organization

| Category | Example Tools |
|----------|---------------|
| **Communication** | Slack, Teams, Discord |
| **CRM** | Salesforce, HubSpot, Pipedrive |
| **DevOps** | GitHub, GitLab, Bitbucket |
| **Project Management** | Jira, Asana, Monday |
| **Marketing** | Marketo, Mailchimp, Intercom |
| **Storage** | Google Drive, Dropbox, OneDrive |
| **Analytics** | Segment, Amplitude, Mixpanel |

### Integration Hub Categories

```
✓ "DevOps & Engineering"
   Connect your development workflow

   GitHub • GitLab • Bitbucket • Jenkins • CircleCI
   [See all DevOps integrations →]

✓ "Communication"
   Stay informed where you work

   Slack • Microsoft Teams • Discord • Email
   [See all communication integrations →]
```

### SEO Optimization

| Element | Best Practice |
|---------|---------------|
| **Title** | "[Your Product] [Tool] Integration" |
| **Meta** | "Connect [Your Product] with [Tool]. Sync [data types], automate workflows..." |
| **H1** | "[Your Product] + [Tool]" |
| **URL** | /integrations/[tool-name] |
| **Alt text** | "[Your Product] and [Tool] logos" |

### Integration Page Checklist

- [ ] Headline uses both product names
- [ ] Logos for both products displayed
- [ ] Benefits are integration-specific, not generic
- [ ] Setup steps are clear and numbered
- [ ] Technical details for evaluators
- [ ] Testimonial from user of this integration
- [ ] Related integrations cross-linked
- [ ] CTA matches user's likely account status
- [ ] SEO elements optimized
- [ ] Page stays updated when integration changes

### Anti-Patterns

- **Generic benefits** — "Sync your data" means nothing
- **Missing logos** — Visual recognition matters
- **No setup info** — How hard is it to connect?
- **Technical-only** — Balance tech details with user value
- **Outdated pages** — Old screenshots, deprecated features
- **No use cases** — Show what becomes possible
- **Isolated pages** — Cross-link related integrations
- **Missing requirements** — What plan/version is needed?
- **No testimonials** — Integration-specific proof helps
- **Buried in navigation** — Make integrations easy to find
