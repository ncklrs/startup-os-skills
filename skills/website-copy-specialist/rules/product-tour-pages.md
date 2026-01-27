---
title: Product Tour Pages
impact: HIGH
tags: product-tour, demo, walkthrough, visual-demo
---

## Product Tour Pages

**Impact: HIGH**

Product tour pages show your product in action before signup. They reduce the friction of "I need to see it first" and give visitors confidence about what they're getting into.

### Product Tour Types

| Type | Format | Best For |
|------|--------|----------|
| **Interactive demo** | Clickable prototype | Complex products |
| **Video tour** | 2-5 minute walkthrough | Story-driven products |
| **Screenshot tour** | Guided visual flow | Simple products |
| **Live sandbox** | Read-only product access | Technical products |
| **Animated walkthrough** | Motion-based tour | Visual products |

### Product Tour Structure

```
┌────────────────────────────────────────────────────┐
│ 1. INTRO/HOOK                                      │
│    What they'll see + time commitment              │
│    "See how [Product] works in 3 minutes"          │
├────────────────────────────────────────────────────┤
│ 2. KEY WORKFLOW #1                                 │
│    Core job-to-be-done                             │
│    Setup or getting started flow                   │
├────────────────────────────────────────────────────┤
│ 3. KEY WORKFLOW #2                                 │
│    Primary value moment                            │
│    "This is where the magic happens"               │
├────────────────────────────────────────────────────┤
│ 4. KEY WORKFLOW #3                                 │
│    Secondary value or collaboration                │
│    Team features, sharing, results                 │
├────────────────────────────────────────────────────┤
│ 5. OUTCOME                                         │
│    What they've accomplished                       │
│    Results or deliverable                          │
├────────────────────────────────────────────────────┤
│ 6. CTA                                             │
│    "Start free" or "Try it yourself"               │
└────────────────────────────────────────────────────┘
```

### Tour Page Headlines

| Formula | Example | Tone |
|---------|---------|------|
| **See [Product] in action** | "See Acme in action" | Direct |
| **[Time] tour** | "A 3-minute tour of Acme" | Time commitment |
| **How [Product] works** | "How Acme works" | Educational |
| **Experience [Product]** | "Experience the Acme difference" | Experiential |

### Good Tour Headlines

```
✓ "See how teams ship faster with Acme"
  → Outcome-focused, audience clarity

✓ "A 3-minute tour of your new workspace"
  → Time commitment + ownership language

✓ "Watch: From zero to deployed in 5 minutes"
  → Specific outcome, time-based

✓ "Take Acme for a spin"
  → Casual, low-pressure
```

### Bad Tour Headlines

```
✗ "Product Demo"
  → Generic, no value proposition

✗ "Watch Our Amazing Features"
  → Self-congratulatory

✗ "Welcome to the Acme Experience"
  → Vague, no clear expectation

✗ "Click Here to Learn More"
  → Not a headline, weak CTA
```

### Writing Tour Narration/Copy

Each tour step needs:
1. **What they're seeing** (orient the viewer)
2. **Why it matters** (connect to their goal)
3. **What to notice** (guide attention)

### Good Tour Step Copy

```
✓ Step 1: "Connect your repository"
   "Start by connecting your GitHub repo. One click, and Acme
   automatically syncs with every branch. No config files needed."
   [Screenshot showing GitHub connection UI]

✓ Step 2: "See your first insights"
   "Within seconds, you'll see code quality metrics across your
   entire codebase. Spot issues before they become problems."
   [Screenshot showing dashboard with metrics]

✓ Step 3: "Share with your team"
   "Invite teammates in seconds. Everyone sees the same view,
   comments stay connected to the code."
   [Screenshot showing team invitation flow]
```

### Bad Tour Step Copy

```
✗ "Step 1: Here is the dashboard"
   → No value, just labeling

✗ "This is our powerful integration engine"
   → About you, not them

✗ "Next, click the blue button"
   → Instructions without value

✗ "As you can see, there are many features here"
   → Vague, unfocused
```

### Screenshot Guidelines

| Element | Best Practice |
|---------|---------------|
| **Size** | Large enough to read key UI elements |
| **Focus** | Highlight the relevant area (blur or dim surroundings) |
| **Data** | Use realistic, relatable sample data |
| **Annotations** | Arrows or callouts for complex screens |
| **Sequence** | Clear visual flow between steps |
| **Freshness** | Update when UI changes |

### Good Screenshot Practices

```
✓ Show realistic data
   Project names like "Q4 Marketing Campaign" not "Test Project 1"

✓ Highlight the focus area
   Dim or blur irrelevant parts of the screen

✓ Use callouts sparingly
   One arrow pointing to the key element

✓ Show before/after
   Empty state → filled state progression

✓ Include realistic team members
   "Sarah (Marketing)" not "User 1"
```

### Bad Screenshot Practices

```
✗ Empty or dummy data
   "Lorem ipsum" or "Test data here"

✗ Cluttered annotations
   10 arrows pointing everywhere

✗ Full screenshot with no focus
   Everything equally visible

✗ Outdated UI
   Screenshots from 3 versions ago

✗ Admin/debug views
   Technical screens normal users won't see
```

### Video Tour Best Practices

| Element | Guideline |
|---------|-----------|
| **Length** | 2-4 minutes optimal |
| **Pace** | Fast enough to hold attention, slow enough to follow |
| **Audio** | Professional voiceover or on-screen text |
| **Music** | Subtle background, never overpowering |
| **Resolution** | 1080p minimum, 4K preferred |
| **Captions** | Always include (many watch muted) |

### Good Video Structure

```
✓ 0:00-0:15 — Hook: The problem/outcome
   "Tired of losing track of customer requests?"

✓ 0:15-1:00 — Setup: Quick context
   "Let me show you how Acme solves this in 3 steps"

✓ 1:00-3:00 — Core workflow
   Show the primary use case, narrate value

✓ 3:00-3:30 — Results
   "Now you have a complete view of..."

✓ 3:30-4:00 — CTA
   "Start your free trial at acme.com"
```

### Interactive Demo Guidelines

| Element | Best Practice |
|---------|---------------|
| **Guidance** | Clear tooltips showing next action |
| **Progress** | Indicator showing tour position |
| **Skip option** | Let users jump ahead or exit |
| **Reset option** | Way to start over |
| **Real feel** | Mimics actual product closely |
| **Limitations** | Clear what's demo vs full product |

### Good Interactive Demo Copy

```
✓ Tooltip: "Click here to create your first project"
   Hint: In the real product, you can create unlimited projects.

✓ Progress: "Step 2 of 5: Setting up integrations"

✓ Callout: "This is where your team's activity appears"
   Notice how every action is timestamped and attributed.

✓ End screen: "That's the basics! Ready to try the real thing?"
   [Start free trial] [Replay tour]
```

### Tour Completion CTAs

| Tour Type | Primary CTA | Secondary CTA |
|-----------|-------------|---------------|
| **Video** | "Start free trial" | "Watch more videos" |
| **Interactive** | "Try it yourself" | "Book a demo" |
| **Screenshot** | "Get started free" | "See pricing" |
| **Sandbox** | "Create your account" | "Talk to sales" |

### Good Tour CTAs

```
✓ After video: "Ready to try it yourself?"
   [Start free trial — no credit card required]

✓ After interactive: "That was just a preview"
   [Create your free account and explore everything]

✓ After screenshot tour: "Seeing is believing"
   [Start free] or [Book a personalized demo]
```

### Tour Page Metrics

| Metric | Target | What It Measures |
|--------|--------|------------------|
| **Completion rate** | >60% | Tour engagement |
| **Time on page** | 2-5 min | Content quality |
| **CTA click rate** | >10% | Persuasiveness |
| **Drop-off points** | N/A | Content issues |

### Tour Page Checklist

- [ ] Headline sets clear expectation (time, content)
- [ ] Tour follows logical workflow
- [ ] Each step has value-focused copy
- [ ] Screenshots/videos use realistic data
- [ ] Focus areas are highlighted
- [ ] Progress indicator shows position
- [ ] Skip/exit options available
- [ ] CTA appears at end and optionally throughout
- [ ] Mobile experience is considered
- [ ] Tour stays updated with product changes

### Anti-Patterns

- **Feature parade** — Tours should follow workflows, not feature lists
- **No context** — Don't show screens without explaining why they matter
- **Stale content** — Outdated screenshots erode trust
- **Too long** — Attention drops after 4-5 minutes
- **No clear CTA** — Tour should lead somewhere
- **Forced completion** — Let people skip or exit
- **Technical jargon** — Tours are for prospects, not power users
- **Perfect scenarios** — Show realistic use, not idealized demos
- **Missing audio/captions** — Many watch without sound
- **Desktop only** — Consider mobile viewers
