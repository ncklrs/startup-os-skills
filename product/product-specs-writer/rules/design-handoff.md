---
title: Design Handoff Documentation
impact: MEDIUM-HIGH
tags: design, handoff, ui, ux, components, specifications
---

## Design Handoff Documentation

**Impact: MEDIUM-HIGH**

Design handoff docs bridge the gap between design files and working code. They translate visual designs into implementable specifications, preventing the "that's not what I meant" rework cycle.

### Design Handoff Components

| Component | Purpose | Who Creates |
|-----------|---------|-------------|
| **Component Specs** | Individual UI element details | Designer |
| **Interaction Specs** | Behaviors, transitions, animations | Designer |
| **Responsive Specs** | Breakpoints, layout changes | Designer |
| **Content Specs** | Copy, microcopy, character limits | Product/Design |
| **Accessibility Specs** | WCAG requirements, screen reader | Designer |
| **Asset Handoff** | Icons, images, fonts | Designer |
| **Edge State Specs** | Loading, empty, error states | Product/Design |

### Component Specification Template

```markdown
## Component: [Name]

### Visual Reference
[Screenshot or Figma link]

### Properties

| Property | Type | Default | Options |
|----------|------|---------|---------|
| variant | string | "primary" | primary, secondary, ghost |
| size | string | "medium" | small, medium, large |
| disabled | boolean | false | - |
| loading | boolean | false | - |
| icon | string | null | icon name or null |
| fullWidth | boolean | false | - |

### Anatomy

[Diagram showing component parts]

| Part | Token/Value | Notes |
|------|-------------|-------|
| Container | padding-x: 16px, padding-y: 8px | |
| Text | font-body-medium | Truncate with ellipsis |
| Icon | 20x20px | Left-aligned, 8px gap |
| Border | 1px solid gray-300 | Only for secondary |

### States

| State | Visual Change | Token |
|-------|---------------|-------|
| Default | - | bg-primary |
| Hover | Darken 10% | bg-primary-hover |
| Active | Darken 20% | bg-primary-active |
| Focus | 2px ring | ring-focus |
| Disabled | 50% opacity | opacity-50 |
| Loading | Spinner replaces text | - |

### Responsive Behavior

| Breakpoint | Behavior |
|------------|----------|
| Mobile (<640px) | Full width, stacked icons |
| Tablet (640-1024px) | Auto width, inline icons |
| Desktop (>1024px) | Fixed width options available |

### Accessibility

- Role: button
- Keyboard: Enter/Space to activate
- Focus: Visible focus ring
- Screen reader: Announce loading state
- Color contrast: Minimum 4.5:1

### Usage Guidelines

**Do:**
- Use primary for main actions
- One primary button per section
- Use loading state for async actions

**Don't:**
- Don't use multiple primary buttons together
- Don't disable without explaining why
- Don't use ghost for important actions
```

### Good Design Handoff Example

```markdown
# Design Handoff: Workspace Invitation Modal

## Overview
Modal for workspace owners to invite new team members. Appears when
clicking "Invite" button in workspace header.

**Figma:** [Link to designs]
**Prototype:** [Link to prototype]

## Modal Container

| Property | Value | Token |
|----------|-------|-------|
| Width | 480px | - |
| Max Height | 80vh | - |
| Padding | 24px | spacing-6 |
| Border Radius | 12px | radius-lg |
| Background | White | bg-surface |
| Shadow | Large | shadow-lg |
| Backdrop | 50% black | overlay-50 |

### Animation

| Action | Animation |
|--------|-----------|
| Open | Fade in (200ms) + scale from 95% |
| Close | Fade out (150ms) |
| Backdrop click | Close modal |
| Escape key | Close modal |

## Header Section

```
┌─────────────────────────────────────────┐
│ [Icon] Invite to Workspace          [X] │
│ Add team members to "Q4 Planning"       │
└─────────────────────────────────────────┘
```

| Element | Spec |
|---------|------|
| Title | text-lg, font-semibold, gray-900 |
| Subtitle | text-sm, gray-600 |
| Close button | 24x24, gray-500, hover: gray-700 |
| Icon | 20x20, primary color |
| Gap between title/subtitle | 4px |

## Form Section

### Email Input

| Property | Value |
|----------|-------|
| Label | "Email address" |
| Placeholder | "colleague@company.com" |
| Type | email |
| Validation | Real-time email format |
| Error | Inline, below input |

**States:**
| State | Border | Background | Text |
|-------|--------|------------|------|
| Default | gray-300 | white | gray-900 |
| Focus | primary-500 | white | gray-900 |
| Error | red-500 | red-50 | gray-900 |
| Disabled | gray-200 | gray-50 | gray-500 |

### Permission Dropdown

| Property | Value |
|----------|-------|
| Label | "Permission level" |
| Default | "Editor" |
| Options | Viewer, Editor, Owner |
| Width | Full width |

**Option Display:**
```
┌─────────────────────────────────┐
│ Editor                       ▼  │
├─────────────────────────────────┤
│ Viewer                          │
│ Can view content                │
├─────────────────────────────────┤
│ Editor                      ✓   │
│ Can view and edit content       │
├─────────────────────────────────┤
│ Owner                           │
│ Full access including settings  │
└─────────────────────────────────┘
```

### Optional Message (Collapsed by Default)

| Property | Value |
|----------|-------|
| Toggle | "Add a personal message" link |
| Textarea | 3 rows default, auto-expand |
| Character limit | 500 |
| Counter | "0/500" aligned right |

## Footer Section

```
┌─────────────────────────────────────────┐
│                    [Cancel] [Send Invite]│
└─────────────────────────────────────────┘
```

| Button | Variant | Behavior |
|--------|---------|----------|
| Cancel | Ghost | Close modal, no action |
| Send Invite | Primary | Validate, submit, close |

**Button States:**
| State | Send Invite |
|-------|-------------|
| Default | Enabled |
| Invalid form | Disabled, tooltip: "Enter valid email" |
| Submitting | Loading spinner, text: "Sending..." |
| Success | Close modal, show toast |

## Edge States

### Empty State
N/A (modal always has form)

### Loading State
While checking if email is already member:
- Show spinner in email input
- Disable submit button

### Error States

| Error | Display |
|-------|---------|
| Invalid email | Inline error: "Please enter a valid email" |
| Already member | Inline error: "This person is already a member" |
| Invitation pending | Inline warning: "Invitation pending. Resend?" |
| Workspace full | Banner at top: "Member limit reached (50/50)" |
| Network error | Toast: "Couldn't send. Check connection." |

### Success State
- Modal closes
- Toast: "Invitation sent to colleague@company.com"
- Members list updates (if visible)

## Responsive Behavior

| Breakpoint | Changes |
|------------|---------|
| Desktop (>768px) | Centered modal, 480px width |
| Tablet (640-768px) | Centered modal, 90% width |
| Mobile (<640px) | Full screen drawer from bottom |

### Mobile Drawer Specifics
- Slides up from bottom
- Full width, rounded top corners
- Max height 90vh
- Handle bar at top for drag-to-close

## Accessibility Checklist

- [ ] Focus trapped inside modal when open
- [ ] First focusable element (email input) auto-focused
- [ ] Escape key closes modal
- [ ] aria-labelledby points to title
- [ ] aria-describedby points to subtitle
- [ ] Close button has aria-label="Close"
- [ ] Form inputs have associated labels
- [ ] Error messages linked with aria-describedby
- [ ] Submit button announces loading state

## Content Specifications

| Element | Copy | Character Limit |
|---------|------|-----------------|
| Modal title | "Invite to Workspace" | 30 |
| Subtitle | "Add team members to [Workspace Name]" | Dynamic |
| Email label | "Email address" | - |
| Email placeholder | "colleague@company.com" | - |
| Permission label | "Permission level" | - |
| Message toggle | "Add a personal message" | - |
| Cancel button | "Cancel" | - |
| Submit button | "Send Invite" | - |
| Submit loading | "Sending..." | - |
| Success toast | "Invitation sent to [email]" | Dynamic |

## Assets Required

| Asset | Format | Sizes |
|-------|--------|-------|
| Invite icon | SVG | 20x20 |
| Close icon | SVG | 24x24 |
| Dropdown arrow | SVG | 12x12 |
| Checkmark | SVG | 16x16 |
| Spinner | SVG/CSS | 16x16 |

## Implementation Notes

- Use existing Modal component from design system
- Email validation should match backend regex
- Debounce email check (500ms) to reduce API calls
- Pre-fill email if inviting from contact list
```

### Bad Design Handoff Example

```markdown
# Invitation Modal

See Figma for designs.

Buttons should work.
Make it look good on mobile.
```

**Why it fails:**
- No specifications, just pointers
- No states or interactions documented
- No responsive behavior details
- No accessibility requirements
- No content specifications

### Design Token Reference

Include token mappings for consistency:

```markdown
## Design Tokens Reference

### Spacing
| Token | Value | Use |
|-------|-------|-----|
| spacing-1 | 4px | Tight grouping |
| spacing-2 | 8px | Related elements |
| spacing-4 | 16px | Section padding |
| spacing-6 | 24px | Large gaps |

### Typography
| Token | Value | Use |
|-------|-------|-----|
| text-xs | 12px/16px | Captions |
| text-sm | 14px/20px | Secondary text |
| text-base | 16px/24px | Body |
| text-lg | 18px/28px | Subheadings |
| text-xl | 20px/28px | Headings |

### Colors
| Token | Value | Use |
|-------|-------|-----|
| gray-50 | #F9FAFB | Background |
| gray-500 | #6B7280 | Secondary text |
| gray-900 | #111827 | Primary text |
| primary-500 | #3B82F6 | Primary actions |
| red-500 | #EF4444 | Errors |
| green-500 | #22C55E | Success |
```

### Handoff Checklist

```
Visual Specs
├── □ All states documented (default, hover, active, focus, disabled)
├── □ Spacing and dimensions specified
├── □ Typography tokens referenced
├── □ Color tokens referenced
├── □ Border radius and shadows noted

Interaction Specs
├── □ Animations/transitions defined
├── □ Keyboard interactions noted
├── □ Touch interactions noted
├── □ Loading states designed
├── □ Error states designed
├── □ Empty states designed

Responsive Specs
├── □ Breakpoints defined
├── □ Layout changes per breakpoint
├── □ Touch target sizes verified (min 44px)

Accessibility Specs
├── □ Color contrast verified (4.5:1 text, 3:1 UI)
├── □ Focus states visible
├── □ Screen reader content specified
├── □ Keyboard navigation flow defined

Content Specs
├── □ All copy provided
├── □ Character limits defined
├── □ Error messages written
├── □ Success messages written

Assets
├── □ Icons exported (SVG)
├── □ Images exported (proper formats/sizes)
├── □ Fonts documented
```

### Anti-Patterns

- **Figma-only handoff** — "Everything is in Figma" (engineering shouldn't have to interpret)
- **Missing states** — Only designing happy path, no loading/error/empty
- **Pixel-perfect tyranny** — Specs so rigid they ignore platform conventions
- **No responsive specs** — Desktop designs with "make it work on mobile"
- **Accessibility afterthought** — No a11y specs until audit fails
- **Undocumented animations** — "It should feel smooth" without timing
- **Missing content** — Lorem ipsum in production
- **No edge cases** — What happens with 100 characters? 1000?
- **Stale handoffs** — Designs change, specs don't update
