---
title: Navigation and Microcopy
impact: MEDIUM
tags: navigation, microcopy, ux-writing, buttons, labels
---

## Navigation and Microcopy

**Impact: MEDIUM**

Microcopy is the small text that guides users through your site — navigation labels, button text, form hints, error messages, and empty states. It's invisible when done well and frustrating when done poorly.

### Types of Microcopy

| Type | Examples | Purpose |
|------|----------|---------|
| **Navigation** | Menu labels, breadcrumbs | Wayfinding |
| **Buttons** | CTAs, form submits | Action guidance |
| **Form labels** | Field names, hints, errors | Input assistance |
| **Empty states** | No results, first-use | Reduce confusion |
| **Tooltips** | Hover explanations | Contextual help |
| **Confirmation** | Success messages | Closure and next steps |
| **Loading/Progress** | Processing messages | Patience and trust |

### Navigation Label Principles

| Principle | Example |
|-----------|---------|
| **Clarity over cleverness** | "Pricing" not "Investment" |
| **Nouns for destinations** | "Features" not "Explore Features" |
| **Consistency** | Same word, same meaning |
| **Parallel structure** | "Products", "Pricing", "Resources" |
| **User mental models** | Use expected terms |

### Good Navigation Labels

```
✓ Main navigation:
   Product | Pricing | Customers | Resources | Company

✓ Footer navigation:
   Product: Features, Integrations, Security, Changelog
   Company: About, Careers, Press, Contact
   Resources: Blog, Help Center, API Docs, Status

✓ Dropdown menu:
   Resources
   ├── Blog
   ├── Help Center
   ├── API Documentation
   ├── Community
   └── What's New
```

### Bad Navigation Labels

```
✗ "Discover" (discover what?)
✗ "Solutions" without context (too vague)
✗ "Hub" (hub of what?)
✗ "Explore Our Offerings" (too wordy)
✗ "Innovation Center" (corporate speak)
✗ "Start Your Journey" (for a nav item)
```

### Navigation Structure Patterns

| Pattern | When to Use | Example |
|---------|-------------|---------|
| **Simple** | Few pages, clear product | Product, Pricing, Docs |
| **Audience-based** | Multiple personas | For Engineers, For Teams |
| **Product-based** | Multiple products | Platform, Apps, Enterprise |
| **Use case-based** | Solution selling | Use Cases, Industries |

### Good Navigation Hierarchies

```
✓ Simple SaaS:
   [Logo] Product • Pricing • Docs • Blog     [Login] [Sign Up]

✓ Platform company:
   [Logo] Products ▾ • Solutions ▾ • Resources ▾ • Pricing     [Login] [Get Started]

✓ Enterprise:
   [Logo] Platform • Solutions • Customers • Resources • Company     [Contact Sales]
```

### Button Copy Principles

| Principle | Bad | Good |
|-----------|-----|------|
| **Be specific** | "Submit" | "Send message" |
| **Lead with verb** | "Your trial" | "Start trial" |
| **Match expectation** | "Go" | "Search" |
| **Show value** | "Next" | "See results" |
| **Reduce anxiety** | "Buy now" | "Start free trial" |

### Button Copy by Action

| Action | Generic (Avoid) | Specific (Better) |
|--------|-----------------|-------------------|
| **Sign up** | "Submit" | "Create account" |
| **Start trial** | "Start" | "Start 14-day trial" |
| **Demo** | "Contact" | "Book a demo" |
| **Download** | "Get it" | "Download PDF" |
| **Subscribe** | "Submit" | "Subscribe to updates" |
| **Search** | "Go" | "Search docs" |
| **Save** | "Save" | "Save changes" |
| **Delete** | "Delete" | "Delete project" |

### Good Button Copy

```
✓ Primary actions:
   "Start free trial"
   "Get started — it's free"
   "Create your account"
   "Book a demo"

✓ Secondary actions:
   "See how it works"
   "View pricing"
   "Read the docs"
   "Talk to sales"

✓ Form submissions:
   "Send message"
   "Subscribe"
   "Save changes"
   "Apply filters"
```

### Bad Button Copy

```
✗ "Submit" (submit what?)
✗ "Click here" (obvious)
✗ "Go" (go where?)
✗ "Yes" / "No" (for complex actions)
✗ "Process" (what happens?)
✗ "Continue" (without context)
```

### Form Microcopy

| Element | Purpose | Example |
|---------|---------|---------|
| **Label** | Identify the field | "Email address" |
| **Placeholder** | Show format | "you@company.com" |
| **Hint text** | Provide guidance | "We'll never share your email" |
| **Error message** | Explain problem + fix | "Email is required" |
| **Success message** | Confirm completion | "Email verified" |

### Good Form Microcopy

```
✓ Email
   [you@company.com________________]
   We'll use this to send your login details

✓ Password
   [••••••••••••••________________]
   At least 8 characters with one number

✓ Error:
   ⚠ "Please enter a valid email address"

✓ Success:
   ✓ "Your account has been created. Check your email to verify."
```

### Bad Form Microcopy

```
✗ EMAIL: (all caps, unfriendly)
✗ [Enter email here] (redundant placeholder)
✗ Error: "Invalid input" (unhelpful)
✗ "Error 422: Validation failed" (technical)
✗ No hint text at all (leaves users guessing)
```

### Error Message Formula

```
What went wrong + How to fix it

✓ "That email is already registered. Try logging in instead."
✓ "Password must be at least 8 characters."
✓ "We couldn't process your payment. Please check your card details."

✗ "Error"
✗ "Invalid"
✗ "Something went wrong"
✗ "Please try again"
```

### Empty State Microcopy

| Scenario | What to Include |
|----------|-----------------|
| **First use** | What this area is for + how to start |
| **No results** | Why empty + what to try |
| **Filtered empty** | Suggest adjusting filters |
| **Error state** | What happened + what to do |

### Good Empty States

```
✓ First project:
   "No projects yet"
   Projects help you organize your work. Create your first one
   to get started.
   [Create project]

✓ No search results:
   "No results for 'xyz'"
   Try adjusting your search or browse all items.
   [Clear search] [Browse all]

✓ Empty dashboard:
   "Nothing here yet"
   Once your team starts using Acme, you'll see activity here.
   [Invite your team]
```

### Bad Empty States

```
✗ "No data"
   → Unhelpful, no guidance

✗ "0 results found"
   → Technical, no next step

✗ [Blank space with no message]
   → Confusing, broken-feeling
```

### Tooltip Microcopy

| Principle | Example |
|-----------|---------|
| **Brief** | Under 100 characters |
| **Helpful** | Answers "What is this?" |
| **Avoid obvious** | Don't tooltip "Save" with "Saves your work" |
| **Add value** | Include shortcuts, tips |

### Good Tooltips

```
✓ [?] "Daily active users who completed at least one action"
✓ [?] "Press ⌘K to open quick search"
✓ [?] "This setting affects all team members"
```

### Bad Tooltips

```
✗ [?] "Click this button" (obvious)
✗ [?] "This is the save button" (obvious)
✗ [?] A full paragraph of explanation (too long)
```

### Confirmation Messages

| Action | Confirmation |
|--------|--------------|
| **Save** | "Changes saved" |
| **Delete** | "Project deleted" (with undo option) |
| **Send** | "Message sent" |
| **Subscribe** | "You're subscribed! Check your email" |
| **Form submit** | "Thanks! We'll be in touch within 24 hours" |

### Good Confirmation Messages

```
✓ "Changes saved"
   Brief, appears near the action

✓ "Message sent! We'll respond within 1 business day"
   Confirms action + sets expectation

✓ "Project deleted" [Undo]
   Acknowledges + offers recovery

✓ "Welcome to Acme! Check your email to get started"
   Confirms + provides next step
```

### Loading State Microcopy

| Duration | Message Style |
|----------|---------------|
| **< 2 seconds** | Spinner only, no text |
| **2-5 seconds** | "Loading..." or specific action |
| **5-10 seconds** | "This might take a moment..." |
| **10+ seconds** | Progress indicator + estimate |

### Good Loading Messages

```
✓ "Generating your report..."
✓ "Syncing your data... this usually takes about 30 seconds"
✓ "Almost there..."
✓ [Progress bar] "Processing 47 of 100 items"
```

### Microcopy Voice Guidelines

| Context | Tone | Example |
|---------|------|---------|
| **Success** | Positive, brief | "You're all set!" |
| **Error** | Helpful, not blaming | "Hmm, that didn't work" |
| **Waiting** | Patient, reassuring | "Just a moment..." |
| **Empty** | Encouraging, guiding | "You're off to a great start" |
| **Destructive** | Clear, confirming | "Delete project? This can't be undone" |

### Microcopy Checklist

- [ ] Navigation labels are clear nouns
- [ ] Buttons lead with verbs
- [ ] Form labels are specific
- [ ] Error messages explain how to fix
- [ ] Empty states guide users forward
- [ ] Success messages confirm and suggest next step
- [ ] Loading states set expectations
- [ ] Tooltips add value, not obvious info
- [ ] Consistent voice across all touchpoints
- [ ] Mobile-appropriate length

### Anti-Patterns

- **"Click here"** — The action should be in the link text
- **"Submit"** — Always specify what's being submitted
- **Technical error codes** — Users don't need error 500 details
- **Blaming language** — "You entered an invalid email"
- **Missing empty states** — Blank areas feel broken
- **Long loading without explanation** — Users think it's frozen
- **Clever over clear** — Puns and jokes that confuse
- **Inconsistent terminology** — "Sign up" vs "Register" vs "Create account"
- **All caps labels** — FEELS LIKE SHOUTING
- **No recovery options** — Delete without undo feels dangerous
