---
title: Acceptance Criteria
impact: CRITICAL
tags: acceptance-criteria, testing, qa, definition-of-done, gherkin
---

## Acceptance Criteria

**Impact: CRITICAL**

Acceptance criteria define the contract between PM, engineering, and QA. They answer: "How do we know this story is done?" Without clear criteria, you get endless debates, missed requirements, and rework.

### Purpose of Acceptance Criteria

1. **Shared understanding** — Everyone agrees what "done" means
2. **Testable conditions** — QA can verify each criterion
3. **Scope boundaries** — Prevents feature creep during development
4. **Estimation input** — Engineers understand complexity upfront

### Given-When-Then Format (Gherkin)

The gold standard for testable acceptance criteria:

```gherkin
Given [precondition/context]
When [action/trigger]
Then [expected outcome]
```

**Multiple Conditions:**
```gherkin
Given [precondition]
  And [additional precondition]
When [action]
Then [outcome]
  And [additional outcome]
  But [exception/exclusion]
```

### Acceptance Criteria Patterns

| Pattern | Use When | Example |
|---------|----------|---------|
| **Happy Path** | Describing normal flow | User logs in successfully |
| **Error State** | Invalid input/failure | Wrong password shows error |
| **Edge Case** | Boundary conditions | Cart with 999 items |
| **Permission** | Access control | Admin-only action blocked for user |
| **State Change** | Before/after conditions | Draft → Published |
| **Performance** | Speed requirements | Page loads in <2 seconds |

### Good Acceptance Criteria Examples

**Feature: Password Reset**

```gherkin
Scenario: Successful password reset request
Given I am on the login page
  And I have a registered account with email "user@example.com"
When I click "Forgot Password"
  And I enter my email address
  And I click "Send Reset Link"
Then I see confirmation message "Check your email for reset instructions"
  And I receive an email within 60 seconds
  And the email contains a unique reset link valid for 24 hours

Scenario: Password reset with unregistered email
Given I am on the forgot password page
When I enter an email not in our system
  And I click "Send Reset Link"
Then I see the same confirmation message (security: don't reveal if email exists)
  And no email is sent

Scenario: Password reset link expiration
Given I requested a password reset more than 24 hours ago
When I click the reset link in my email
Then I see "This link has expired"
  And I see option to request a new reset link

Scenario: New password validation
Given I clicked a valid reset link
When I enter a new password
Then the password must be at least 8 characters
  And contain at least one uppercase letter
  And contain at least one number
  And show strength indicator (weak/medium/strong)

Scenario: Successful password change
Given I entered a valid new password
When I click "Reset Password"
Then my password is updated
  And I am logged in automatically
  And I receive confirmation email
  And all other sessions are invalidated
```

**Feature: Shopping Cart**

```gherkin
Scenario: Add item to empty cart
Given my cart is empty
When I add a product priced at $25.00
Then my cart shows 1 item
  And the subtotal shows $25.00
  And the cart icon shows badge with "1"

Scenario: Add same item multiple times
Given I have 2 units of "Blue Widget" in my cart
When I add another "Blue Widget"
Then my cart shows 3 units of "Blue Widget"
  And the quantity is consolidated (not separate line items)

Scenario: Add item exceeding inventory
Given a product has 5 units in stock
  And I already have 5 in my cart
When I try to add another
Then I see "Maximum available quantity reached"
  And my cart quantity remains at 5

Scenario: Cart persistence across sessions
Given I am logged in with items in my cart
When I log out and log back in
Then my cart items are preserved
  And quantities match what I had before

Scenario: Price change after adding to cart
Given I added an item priced at $50.00
  And the price later changes to $45.00
When I view my cart
Then I see the current price of $45.00
  And I see "Price reduced from $50.00" notice
```

### Bad Acceptance Criteria Examples

**Too Vague:**
```
- User can reset password
- It should be secure
- Good user experience
```
**Why it fails:** Not testable. What does "secure" mean? What's "good"?

**Too Implementation-Specific:**
```
- When POST /api/auth/reset is called with valid email,
  return 200 and insert row into password_reset_tokens table
  with SHA-256 hashed token
```
**Why it fails:** Dictates implementation details. Focus on behavior, not code.

**Missing Edge Cases:**
```
Given I enter my email
When I click reset
Then I get an email
```
**Why it fails:** What if email invalid? What if not registered? What if rate limited?

**Incomplete:**
```
- User can add items to cart
```
**Why it fails:** Add how many? What about inventory limits? Does it persist? What feedback do they see?

### Acceptance Criteria Checklist

For each user story, ensure criteria cover:

```
Functional Requirements
├── □ Happy path (normal success flow)
├── □ Validation (input requirements)
├── □ Error states (what can go wrong)
├── □ Edge cases (boundaries, limits)
├── □ Permissions (who can/cannot)
└── □ State transitions (before/after)

Non-Functional Requirements
├── □ Performance (speed, limits)
├── □ Accessibility (screen reader, keyboard)
├── □ Security (auth, data protection)
└── □ Compatibility (browsers, devices)

User Experience
├── □ Feedback (success/error messages)
├── □ Loading states (spinners, skeletons)
└── □ Empty states (no data scenarios)
```

### Acceptance Criteria Table Format

For simpler features, tables can be effective:

**Login Validation:**

| Input | Expected Result |
|-------|-----------------|
| Valid email + correct password | Login succeeds, redirect to dashboard |
| Valid email + wrong password | "Invalid credentials" error, remain on login |
| Invalid email format | "Please enter valid email" inline error |
| Empty email | "Email is required" inline error |
| Empty password | "Password is required" inline error |
| Account locked (5+ failed attempts) | "Account locked. Reset password or wait 30 min" |
| Unverified email account | "Please verify your email first" + resend option |

### Definition of Done vs Acceptance Criteria

| Concept | Scope | Example |
|---------|-------|---------|
| **Acceptance Criteria** | Per story | "Given X, when Y, then Z" |
| **Definition of Done** | All stories | Code reviewed, tests pass, docs updated |

**Definition of Done (team-wide):**
```
□ All acceptance criteria pass
□ Code reviewed and approved
□ Unit tests written (>80% coverage)
□ Integration tests pass
□ No critical/high security issues
□ Accessibility audit pass
□ Documentation updated
□ Deployed to staging
□ PM sign-off
```

### Writing Criteria for Different Story Types

**UI/Frontend Stories:**
- Include visual states (loading, error, success, empty)
- Specify responsive behavior
- Note animation/transition expectations
- Reference design specs

**API/Backend Stories:**
- Include request/response formats
- Specify error codes and messages
- Define rate limits and quotas
- Note caching behavior

**Integration Stories:**
- Define handoff points
- Specify retry/fallback behavior
- Document timeout expectations
- Clarify data format conversions

### Anti-Patterns

- **Criteria as requirements** — Writing new requirements in AC instead of the story
- **Gold plating** — Adding criteria not related to the story
- **Assumption hiding** — Criteria that assume shared knowledge ("handles the usual cases")
- **Test case masquerading** — Low-level test steps instead of behavior
- **Changing mid-sprint** — Adding criteria after development started
- **Checkbox syndrome** — Criteria so broad they're always "met" ("it works")
- **Missing negatives** — Only happy paths, no error scenarios
- **Copy-paste templates** — Same boilerplate criteria on every story
