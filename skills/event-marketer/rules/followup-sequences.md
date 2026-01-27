---
title: Event Follow-Up Sequences
impact: CRITICAL
tags: follow-up, sequences, nurture, post-event
---

## Event Follow-Up Sequences

**Impact: CRITICAL**

Events generate interest, follow-up generates pipeline. 80% of event leads die in a spreadsheet. Systematic, personalized follow-up turns badge scans into revenue.

### The Follow-Up Speed Imperative

| Follow-Up Timing | Response Rate | Pipeline Impact |
|------------------|---------------|-----------------|
| **Same day** | 4x higher | Maximum |
| **Next day** | 2x higher | High |
| **Within 1 week** | Baseline | Standard |
| **After 1 week** | 0.5x | Minimal |
| **After 2 weeks** | 0.25x | Near zero |

**Rule:** First meaningful follow-up within 24 hours of event end, ideally same day.

### Lead Processing Workflow

```
Event Ends
    │
    ▼
Lead Data Export (Same day)
    │
    ▼
Data Cleaning & Enrichment (Same day)
    │
    ▼
Lead Scoring & Segmentation (Day 1)
    │
    ▼
Route to Sales + Enter Nurture (Day 1-2)
    │
    ├── Hot → SDR/AE personal outreach (Day 1)
    ├── Warm → Semi-personalized sequence (Day 2)
    └── Cold → Marketing nurture (Day 3-5)
    │
    ▼
Track & Measure (Ongoing)
```

### Lead Segmentation for Follow-Up

| Segment | Criteria | Follow-Up Approach |
|---------|----------|-------------------|
| **Hot** | Decision maker, active pain, near-term timeline | AE call + personalized email |
| **Warm** | Influencer or future need, clear interest | SDR sequence + relevant content |
| **Cold** | Practitioner, no timeline, mild interest | Marketing nurture + retargeting |
| **Customer** | Existing customer at booth | CSM handoff + expansion content |
| **Partner** | Potential partnership discussion | BD team handoff |

### Hot Lead Follow-Up (Day 1)

```
Touchpoint 1: Personal email (within 4 hours)
Subject: "Great meeting you at [Event], [First Name]"
─────────────────────────────────────────────────
Hi [First Name],

Thanks for stopping by our booth at [Event]. I enjoyed our conversation
about [specific topic they mentioned].

You mentioned you're dealing with [specific pain point]. I'd love to show
you how [Customer Name] solved a similar challenge — they [specific result].

Are you free [2 specific times] this week for a quick call?

[AE Name]
─────────────────────────────────────────────────

Touchpoint 2: LinkedIn connection (same day)
→ Personalized note referencing conversation

Touchpoint 3: Call attempt (Day 2)
→ If no response to email, call with voicemail

Touchpoint 4: Follow-up email (Day 3)
→ New angle or additional value
```

### Warm Lead Follow-Up Sequence

```
Email 1 (Day 1): Thank you + resource
Subject: "[Event] — the resource I mentioned"
Focus: Deliver promised content, light CTA

Email 2 (Day 3): Case study
Subject: "How [Similar Company] solved [their pain]"
Focus: Social proof matching their situation

Email 3 (Day 6): Educational content
Subject: "[Topic] best practices guide"
Focus: Value delivery, soft CTA

Email 4 (Day 10): Offer
Subject: "Next step on [their specific interest]"
Focus: Meeting or demo offer

Email 5 (Day 14): Break-up
Subject: "Should I close your file?"
Focus: Final attempt, clear opt-out
```

### Cold Lead Nurture Track

```
Email 1 (Day 2): Thank you + recording
Subject: "[Event] resources + our session recording"
Focus: Event value, content consumption

Email 2 (Week 2): Newsletter add
Subject: "You're in: [Newsletter Name]"
Focus: Ongoing value, content delivery

Email 3 (Week 4): Problem-focused content
Subject: "[Industry] teams are struggling with [problem]"
Focus: Problem awareness, thought leadership

→ Continue standard marketing nurture
→ Retarget with event-specific ads
→ Re-engage at next relevant event
```

### Good Follow-Up Emails

```
✓ Subject: "That secrets sprawl problem you mentioned"
  Body references specific conversation, offers specific solution

✓ Subject: "The Stripe case study I promised"
  Delivers value promised during conversation

✓ Subject: "Quick question about your Terraform setup"
  Shows you remember details, positions as helpful

✓ Subject: "[Event] video + your free trial"
  Multiple value elements, clear next step
```

### Bad Follow-Up Emails

```
✗ Subject: "Great meeting you!"
  Body: Generic pitch about product
  → No personalization, could be anyone

✗ Subject: "Following up"
  Body: "Let me know if you want to learn more"
  → No value, no specific ask

✗ Subject: "URGENT: Your [Event] follow-up"
  Body: Standard sales pitch
  → Fake urgency, spammy feel

✗ Subject: "Did you get my last email?"
  Body: Just asking for response
  → Desperate, no new value
```

### Personalization Elements

| Data Point | How to Use |
|------------|------------|
| **Their name** | Subject line, greeting |
| **Company name** | Reference in context |
| **Specific pain mentioned** | Lead with in body |
| **Current tools** | Compare/contrast |
| **Event session attended** | Reference content |
| **Booth conversation topic** | Prove you listened |
| **Demo they saw** | Follow up on questions |

### Follow-Up Content Assets

| Lead Temperature | Content Type | Purpose |
|-----------------|--------------|---------|
| **Hot** | Pricing info, implementation guide | Help them buy |
| **Warm** | Case study, ROI calculator | Build case |
| **Cold** | Educational blog, research | Stay relevant |
| **All** | Event recording, slides | Immediate value |

### Sales + Marketing Handoff

| Lead Type | Owner | SLA | Marketing Support |
|-----------|-------|-----|-------------------|
| **Hot** | AE | Contact within 4 hours | None needed |
| **Warm** | SDR | Contact within 24 hours | Nurture sequence backup |
| **Cold** | Marketing | Enter nurture within 48 hours | Full ownership |

### Follow-Up Tracking

| Metric | What It Measures | Target |
|--------|------------------|--------|
| **Follow-up rate** | % of leads contacted | 100% hot/warm |
| **Response rate** | % who reply | 15-25% |
| **Meeting rate** | % who book meeting | 5-10% |
| **SQL rate** | % who become qualified | 20-30% of meetings |
| **Time to first contact** | Hours after event | <24 hours |

### Event Debrief Framework

| Question | Purpose |
|----------|---------|
| **Lead volume by segment** | Volume assessment |
| **Lead quality vs expectations** | Quality assessment |
| **Top conversations/opportunities** | Best opportunity capture |
| **What worked at booth** | Replicate successes |
| **What didn't work** | Avoid next time |
| **Competitor observations** | Market intelligence |
| **Suggested improvements** | Process improvement |

### CRM Hygiene for Event Leads

| Field | What to Capture | Why It Matters |
|-------|-----------------|----------------|
| **Lead source** | Event name | Attribution |
| **Lead source detail** | Booth, session, dinner | Channel detail |
| **Event date** | When captured | Follow-up timing |
| **Lead notes** | Conversation details | Personalization |
| **Lead score** | Hot/warm/cold | Routing |
| **Assigned to** | Sales owner | Accountability |
| **Follow-up status** | Contacted, meeting, etc. | Tracking |

### Automation Setup

```
Trigger: New lead tagged "Event - [Name]"
    │
    ├── If score = Hot
    │   ├── Notify AE (Slack)
    │   ├── Add to hot lead sequence (1 day delay)
    │   └── Add to ABM retargeting
    │
    ├── If score = Warm
    │   ├── Notify SDR (email)
    │   ├── Add to warm lead sequence
    │   └── Add to general retargeting
    │
    └── If score = Cold
        ├── Add to marketing nurture (3 day delay)
        └── Add to general retargeting
```

### Anti-Patterns

- **Batch and blast** — Same generic email to all leads
- **Waiting for sales** — Marketing assumes sales will handle it
- **No notes, no personalization** — "Great meeting you!" to everyone
- **Over-automation** — Obvious template emails to hot leads
- **No urgency** — Following up 2 weeks later
- **Lead limbo** — Leads sit in spreadsheet, never actioned
- **One and done** — Single follow-up, then abandonment
- **No tracking** — No idea if follow-up happened or worked
