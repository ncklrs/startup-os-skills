---
title: User Story Creation
impact: CRITICAL
tags: user-stories, agile, requirements, personas, jtbd
---

## User Story Creation

**Impact: CRITICAL**

User stories translate business requirements into engineering work. They're not just ticket templates — they're communication tools that capture who benefits, what they need, and why it matters.

### The Story Structure

**Classic Format:**
```
As a [persona/user type]
I want [capability/action]
So that [benefit/value]
```

**Enhanced Format:**
```
As a [persona] with [context/situation]
I want to [action/capability]
So that I can [immediate benefit]
Which enables [business outcome]
```

### The INVEST Criteria

Every user story should be:

| Criteria | Question | Red Flag |
|----------|----------|----------|
| **I**ndependent | Can it ship alone? | "Blocked by Story #47" |
| **N**egotiable | Can scope flex? | Over-specified implementation |
| **V**aluable | Does user benefit? | Technical task disguised as story |
| **E**stimable | Can we size it? | Too vague or too large |
| **S**mall | Fits in a sprint? | Multi-week estimate |
| **T**estable | Can we verify done? | No acceptance criteria |

### Story Sizing Guide

| Size | Days | Characteristics |
|------|------|-----------------|
| **XS** | 0.5 | Config change, copy update |
| **S** | 1-2 | Single component, clear path |
| **M** | 3-5 | Multiple components, some unknowns |
| **L** | 5-8 | Cross-system, needs breakdown |
| **XL** | 8+ | Epic-level, must be split |

**Rule of thumb:** If you can't complete it in one sprint, it's not a story — it's an epic.

### Good User Story Examples

**E-commerce: Add to Cart**
```markdown
**Story:** Add product to shopping cart

**As a** shopper browsing products
**I want to** add items to my cart without leaving the product page
**So that** I can continue browsing without losing my selections

**Acceptance Criteria:**
- Given I'm on a product page with available inventory
  When I click "Add to Cart"
  Then the item is added and cart count updates within 500ms

- Given I'm on a product page with size variants
  When I click "Add to Cart" without selecting a size
  Then I see an inline error prompting size selection

- Given I already have 10 of this item in cart
  When I try to add another
  Then I see a message about quantity limits

**Edge Cases:**
- Product goes out of stock between page load and add
- User is not logged in
- Network failure during add

**Out of Scope:**
- Wishlist functionality
- Product recommendations
- Guest checkout flow
```

**SaaS: Team Invitation**
```markdown
**Story:** Invite team member to workspace

**As a** workspace owner
**I want to** invite colleagues by email
**So that** they can collaborate on projects without creating duplicates

**Acceptance Criteria:**
- Given I have owner permissions
  When I enter a valid email and click "Invite"
  Then an invitation email is sent within 60 seconds

- Given the email is already a workspace member
  When I try to invite them
  Then I see "This person is already a member" message

- Given I've sent an invitation
  When I view pending invitations
  Then I see the email, sent date, and option to resend/revoke

**Technical Notes:**
- Use existing email service (SendGrid)
- Invitations expire after 7 days
- Max 50 members per workspace

**Dependencies:**
- Email template (Design: due June 10)
```

### Bad User Story Examples

**Too Vague:**
```markdown
As a user
I want better search
So that I can find things
```
**Why it fails:** Who is the user? What does "better" mean? What things? No acceptance criteria.

**Too Technical:**
```markdown
As a developer
I want to refactor the auth module to use JWT tokens
So that the code is cleaner
```
**Why it fails:** This is a technical task, not a user story. No user value. Reframe as: "As a user, I want to stay logged in across devices..."

**Too Large:**
```markdown
As an admin
I want to manage all users, roles, permissions, and audit logs
So that I can control access to the system
```
**Why it fails:** This is an epic. Split into: manage users, manage roles, manage permissions, view audit logs.

**Missing Context:**
```markdown
As a user
I want to export data
So that I can use it elsewhere
```
**Why it fails:** Export what data? In what format? What's "elsewhere"? Add: "As a marketing manager, I want to export campaign analytics as CSV so that I can create reports in Excel."

### Persona-Based Story Writing

Define personas before writing stories:

| Persona | Description | Goals | Frustrations |
|---------|-------------|-------|--------------|
| **Admin Amy** | IT administrator, 5+ years | Maintain security, reduce tickets | Manual processes, unclear audit |
| **Power User Paul** | Heavy daily user | Speed, keyboard shortcuts | Friction in common tasks |
| **Newbie Nina** | Just joined, learning | Quick onboarding | Confusing UI, hidden features |
| **Executive Eve** | Occasional user, decision-maker | Quick insights, dashboards | Too much detail, slow reports |

Then write stories from their perspective:
- "As Admin Amy, I want to bulk deactivate users so that offboarding is efficient"
- "As Power User Paul, I want keyboard shortcuts for common actions so that I can work faster"

### Jobs-to-Be-Done Integration

Combine JTBD with user stories:

**JTBD Format:**
```
When [situation/trigger]
I want to [motivation/job]
So I can [expected outcome]
```

**Example:**
```
When I'm preparing for a client meeting in 10 minutes
I want to quickly pull last quarter's metrics
So I can answer questions confidently without fumbling through dashboards
```

This becomes the story:
```
As a sales rep preparing for client meetings
I want to see a one-page summary of key account metrics
So that I can quickly reference performance data during calls
```

### Story Mapping

Organize stories into a map:

```
            ┌─────────────────────────────────────────────────┐
User        │  Discovery  │  Selection  │  Purchase  │ Use   │
Journey     └─────────────────────────────────────────────────┘
                  │             │            │           │
            ┌─────┴─────┐ ┌─────┴─────┐ ┌────┴────┐ ┌────┴────┐
Release 1   │  Search   │ │  Compare  │ │ Checkout│ │Dashboard│
(MVP)       │  Browse   │ │  Details  │ │ Payment │ │ Basic   │
            └───────────┘ └───────────┘ └─────────┘ └─────────┘
                  │             │            │           │
            ┌─────┴─────┐ ┌─────┴─────┐ ┌────┴────┐ ┌────┴────┐
Release 2   │  Filters  │ │  Reviews  │ │ Save CC │ │ Reports │
            │  Sort     │ │  Compare  │ │ Express │ │ Export  │
            └───────────┘ └───────────┘ └─────────┘ └─────────┘
```

### Story Splitting Techniques

When a story is too large, split by:

| Technique | Example |
|-----------|---------|
| **Workflow steps** | Register → Verify email → Set password |
| **Business rules** | Basic validation → Complex validation |
| **Data variations** | Single item → Bulk items |
| **Operations** | Create → Read → Update → Delete |
| **User types** | Admin → User → Guest |
| **Platforms** | Web → Mobile → API |
| **Performance** | Works → Works fast |

### Anti-Patterns

- **Story as task** — "Implement login API" (where's the user value?)
- **Compound stories** — "As a user, I want X and Y and Z" (split them)
- **Gold plating** — Over-specified acceptance criteria that constrain solutions
- **Missing "so that"** — Stories without stated value are features without purpose
- **Copy-paste personas** — "As a user" everywhere instead of specific personas
- **Story as spec** — 500-word stories that leave no room for negotiation
- **Orphan stories** — Stories not connected to epics or goals
- **Zombie stories** — Old stories that linger in backlog, never prioritized or removed
