---
title: Proposal Design & Formatting
impact: MEDIUM-HIGH
tags: design, formatting, layout, visual, branding
---

## Proposal Design & Formatting

**Impact: MEDIUM-HIGH**

Design signals professionalism and makes proposals easier to read. Good formatting can't save bad content, but bad formatting can kill good content.

### The Proposal Design Hierarchy

```
┌─────────────────────────────────────────────────────────────┐
│                    VISUAL HIERARCHY                         │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  [Logo/Header]           ← Brand anchor (every page)        │
│                                                             │
│  SECTION HEADING         ← Highest contrast, largest        │
│                                                             │
│  Subsection Heading      ← Secondary emphasis               │
│                                                             │
│  Body text with key      ← Readable, scannable              │
│  points **highlighted**                                     │
│                                                             │
│  ┌──────────────────┐                                       │
│  │ Tables & data    │    ← Structured information           │
│  └──────────────────┘                                       │
│                                                             │
│  [Page number]           ← Navigation aid                   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Design Principles for Proposals

| Principle | Implementation |
|-----------|----------------|
| **Scannability** | Headers, bullets, whitespace — reader should get 80% by scanning |
| **Consistency** | Same fonts, colors, spacing throughout |
| **Hierarchy** | Important things look important |
| **Professionalism** | Clean, polished, error-free |
| **Accessibility** | Readable fonts, sufficient contrast |

### Good Example: Well-Formatted Section

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  3. SOLUTION OVERVIEW                                       │
│  ════════════════════════════════════════════════════       │
│                                                             │
│  SecretStash Enterprise addresses your three core           │
│  challenges with a unified platform approach.               │
│                                                             │
│  ┌───────────────────────────────────────────────────┐      │
│  │  YOUR CHALLENGE          OUR SOLUTION             │      │
│  ├───────────────────────────────────────────────────┤      │
│  │  Manual rotation         Automated rotation        │      │
│  │  Scattered secrets       Centralized vault         │      │
│  │  Compliance gaps         Audit-ready logging       │      │
│  └───────────────────────────────────────────────────┘      │
│                                                             │
│  KEY CAPABILITIES                                           │
│  ─────────────────                                          │
│                                                             │
│  • Centralized Management — Single pane of glass for        │
│    all secrets across environments                          │
│                                                             │
│  • Automated Rotation — Set policies once, rotate           │
│    forever without manual intervention                      │
│                                                             │
│  • Complete Audit Trail — Every access logged with          │
│    who, what, when for compliance reporting                 │
│                                                             │
│                                              Page 7 of 15   │
└─────────────────────────────────────────────────────────────┘
```

### Bad Example: Poorly Formatted Section

```
3. Solution Overview
SecretStash is a secrets management platform. We provide centralized secrets management, automated rotation, access controls, audit logging, and compliance reporting. Our platform integrates with AWS, Azure, GCP, GitHub, GitLab, Jenkins, CircleCI, Kubernetes, Docker, and many other tools. We support PostgreSQL, MySQL, MSSQL, MongoDB, Redis, and other databases. Our customers include companies in financial services, healthcare, technology, retail, and other industries. We have SOC 2 Type II certification, ISO 27001 certification, HIPAA compliance, and PCI DSS compliance. Our platform is trusted by over 500 companies worldwide including Fortune 500 enterprises and fast-growing startups. We offer 24/7 support, dedicated customer success managers, and comprehensive documentation. Our pricing is competitive and we offer flexible terms including monthly and annual billing options.
```

**Why it fails:**
- Wall of text with no structure
- No visual hierarchy
- Impossible to scan
- Lists embedded in paragraphs
- Everything has equal emphasis (so nothing has emphasis)

### Typography Guidelines

| Element | Recommendation |
|---------|----------------|
| **Headings** | Sans-serif (Arial, Helvetica, Calibri), 14-18pt |
| **Body** | Serif or sans-serif, 10-12pt, 1.15-1.5 line spacing |
| **Minimum font** | Never below 9pt |
| **Font limit** | 2 fonts maximum (heading + body) |
| **Bold** | For emphasis, not entire paragraphs |
| **Italics** | For definitions or light emphasis |
| **ALL CAPS** | Headers only, never body text |

### Color Usage

**Brand colors:**
```
Primary:    Use for headers, key elements
Secondary:  Use for accents, callouts
Neutral:    Use for body text, backgrounds
```

**Color rules:**
- 60/30/10 rule: 60% primary, 30% secondary, 10% accent
- Maintain sufficient contrast (4.5:1 minimum for text)
- Don't use color as only differentiator (accessibility)
- Test printing in grayscale

### Table Formatting

**Good table design:**
```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│   Feature          Foundation   Professional   Enterprise   │
│   ────────────────────────────────────────────────────────  │
│   Users included        50           150       Unlimited    │
│   SSO                   —             ✓            ✓        │
│   Dedicated support     —             ✓            ✓        │
│   On-premise option     —             —            ✓        │
│   ────────────────────────────────────────────────────────  │
│   Annual price      $36,000       $84,000       $156,000    │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Table rules:**
- Clear headers with visual distinction
- Consistent alignment (numbers right, text left)
- Adequate row height
- Highlight recommended option
- Use alternating row colors sparingly

### Whitespace Guidelines

| Element | Spacing |
|---------|---------|
| **Page margins** | 0.75" - 1" all sides |
| **Section spacing** | 24-36pt before major sections |
| **Paragraph spacing** | 6-12pt between paragraphs |
| **Line spacing** | 1.15-1.5 for body text |
| **Bullet spacing** | 6pt between items |

**Rule:** When in doubt, add more whitespace.

### Page Layout Templates

**Cover page:**
```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│                                                             │
│                    [YOUR LOGO]                              │
│                                                             │
│                                                             │
│                                                             │
│           Proposal for [CLIENT NAME]                        │
│                                                             │
│    [Proposal Title Tied to Their Goal]                      │
│                                                             │
│                                                             │
│                                                             │
│                   Prepared for:                             │
│               [Contact Name, Title]                         │
│                                                             │
│                   Prepared by:                              │
│              [Your Name, Title]                             │
│                                                             │
│                  [Date]                                     │
│            Valid through [Date + 30]                        │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Content page:**
```
┌─────────────────────────────────────────────────────────────┐
│ [Your Logo]                          [Client Name] Proposal │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│                                                             │
│             [SECTION CONTENT]                               │
│                                                             │
│                                                             │
│                                                             │
│                                                             │
│                                                             │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│ Confidential                                    Page X of Y │
└─────────────────────────────────────────────────────────────┘
```

### Visual Elements to Include

| Element | Purpose | When to Use |
|---------|---------|-------------|
| **Comparison tables** | Side-by-side evaluation | Pricing, features |
| **Timeline diagrams** | Show project phases | Implementation plans |
| **Process flows** | Explain methodology | Approach sections |
| **Icons** | Visual anchors | Section headers, lists |
| **Charts** | Quantify claims | ROI, metrics |
| **Screenshots** | Show product | Solution sections |
| **Customer logos** | Build credibility | Proof sections |

### File Format & Delivery

| Format | When to Use | Considerations |
|--------|-------------|----------------|
| **PDF** | Default choice | Preserves formatting, universal |
| **Interactive PDF** | Embedded links | Test before sending |
| **Word** | If editing needed | Risk of formatting breaks |
| **Presentation** | In-person delivery | Complement, don't replace written |
| **Web/HTML** | Digital experience | Consider platforms like Qwilr, Proposify |

### Pre-Send Checklist

```
□ Spell check completed (including names!)
□ Client company name correct throughout
□ Page numbers present and correct
□ Table of contents matches actual pages
□ Images load properly (no broken links)
□ Confidential footer present
□ Links work
□ File size reasonable (< 10MB)
□ Print preview looks correct
□ PDF test open on different device
```

### Anti-Patterns

- **Clip art** — Looks amateur; use professional imagery or none
- **Too many colors** — Stick to brand palette
- **Inconsistent spacing** — Creates visual chaos
- **Tiny fonts** — If you need tiny fonts, you have too much content
- **Dense paragraphs** — Break up text; use bullets
- **Low-res images** — Either high quality or don't include
- **Excessive emphasis** — If everything is bold, nothing is bold
- **Missing page numbers** — Makes discussion impossible
