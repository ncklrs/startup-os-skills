---
title: On-Page SEO Optimization
impact: CRITICAL
tags: on-page, meta-tags, titles, headers, content-optimization, keywords
---

## On-Page SEO Optimization

**Impact: CRITICAL**

On-page SEO is where content meets technical optimization. Perfect on-page can't save bad content, but bad on-page can sink great content. Every element should serve both users and search engines.

### On-Page Elements Hierarchy

| Element | Impact | User-Facing | Search-Facing |
|---------|--------|-------------|---------------|
| **Title Tag** | Very High | Browser tab, SERP | Primary ranking signal |
| **H1** | High | Page headline | Content topic signal |
| **Meta Description** | Medium | SERP snippet | Click-through rate |
| **URL** | Medium | Address bar | Topic signal |
| **H2-H6** | Medium | Content structure | Subtopic signals |
| **Body Content** | High | Main content | Topical relevance |
| **Images** | Medium | Visual content | Alt text, file names |
| **Internal Links** | High | Navigation | PageRank flow |
| **Schema** | Medium | Rich snippets | Structured data |

### Title Tag Best Practices

| Rule | Guideline |
|------|-----------|
| **Length** | 50-60 characters (avoid truncation) |
| **Keyword placement** | Primary keyword near the front |
| **Uniqueness** | Every page needs unique title |
| **Brand** | Include brand name (usually at end) |
| **Readability** | Must make sense to humans |

### Good Title Tags

```
✓ "Kubernetes Secrets Management: Complete Guide (2024) | Infisical"
  └── Keyword first, year for freshness, brand at end
  └── 62 chars (slight truncation OK)

✓ "HashiCorp Vault vs AWS Secrets Manager: Full Comparison"
  └── Comparison keyword pattern, clear intent

✓ "How to Rotate API Keys Automatically | Step-by-Step Guide"
  └── How-to format, action-oriented
```

### Bad Title Tags

```
✗ "Home"
  └── No keyword, no value, no differentiation

✗ "Secrets Management | Secret Management | Manage Secrets | Infisical"
  └── Keyword stuffing, unreadable

✗ "The Ultimate Comprehensive Complete Guide to Everything You Need to Know About Secrets Management in 2024"
  └── Way too long, will truncate badly

✗ "Infisical - Secrets Management"
  └── Brand first (wastes prime keyword space)
```

### Meta Description Guidelines

| Rule | Guideline |
|------|-----------|
| **Length** | 150-160 characters |
| **Purpose** | Sell the click, not the product |
| **Keywords** | Include naturally (bolded in SERP) |
| **CTA** | Soft call-to-action when appropriate |
| **Unique** | Every page needs unique description |

### Good Meta Descriptions

```
✓ "Learn how to manage secrets in Kubernetes with encryption,
   rotation, and access controls. Step-by-step guide with
   code examples for production environments."

   └── Keywords included naturally
   └── Clear value proposition
   └── Specific (mentions what they'll learn)

✓ "Compare HashiCorp Vault and AWS Secrets Manager side-by-side.
   Features, pricing, security models, and which to choose for
   your infrastructure."

   └── Addresses search intent directly
   └── Lists what comparison covers
```

### Bad Meta Descriptions

```
✗ "Welcome to our website. We provide secrets management
   solutions for businesses of all sizes."

   └── Generic, no value, doesn't match search intent

✗ "secrets management kubernetes docker secrets vault aws
   secrets manager api keys environment variables .env"

   └── Keyword stuffing, unreadable

✗ [No meta description]
   └── Google will pull random text, likely poor
```

### URL Structure

| Element | Best Practice |
|---------|---------------|
| **Length** | Keep short (3-5 words after domain) |
| **Keywords** | Include primary keyword |
| **Separators** | Use hyphens, not underscores |
| **Case** | Lowercase only |
| **Parameters** | Avoid when possible |

### Good URLs

```
✓ /guides/kubernetes-secrets-management
✓ /blog/vault-vs-aws-secrets-manager
✓ /docs/api-key-rotation
✓ /integrations/github-actions
```

### Bad URLs

```
✗ /page?id=12345&category=secrets
✗ /blog/2024/01/15/the-complete-ultimate-guide-to-secrets-management-for-developers
✗ /Blog/Kubernetes_Secrets
✗ /content/article/secrets/management/guide/overview/index.html
```

### Header Structure (H1-H6)

```
H1: Main page title (one per page, matches title tag intent)
│
├── H2: Major section
│   ├── H3: Subsection
│   │   └── H4: Detail (rarely needed)
│   └── H3: Subsection
│
├── H2: Major section
│   └── H3: Subsection
│
└── H2: Major section
```

### Good Header Structure

```markdown
# Kubernetes Secrets Management Guide (H1)

## What Are Kubernetes Secrets? (H2)

## Why Native K8s Secrets Are Risky (H2)

### Base64 is Not Encryption (H3)

### No Access Controls (H3)

## Better Approaches to K8s Secrets (H2)

### External Secrets Operators (H3)

### Dedicated Secrets Managers (H3)

## Implementation Guide (H2)

### Prerequisites (H3)

### Step 1: Install the Operator (H3)

### Step 2: Configure Access (H3)
```

### Bad Header Structure

```markdown
✗ No H1 on page

✗ Multiple H1s:
  # Secrets
  # Management
  # Guide

✗ Skipping levels:
  # Main Title (H1)
  #### Jumped to H4

✗ Headers that don't describe content:
  ## Section 1
  ## Section 2
  ## Read More
```

### Content Optimization Checklist

**Keyword Usage:**
- [ ] Primary keyword in first 100 words
- [ ] Primary keyword in H1 (natural variation OK)
- [ ] Primary keyword in at least one H2
- [ ] Secondary keywords distributed naturally
- [ ] No keyword stuffing (1-2% density max)

**Readability:**
- [ ] Paragraphs 2-4 sentences max
- [ ] Subheadings every 200-300 words
- [ ] Bullet/numbered lists for 3+ items
- [ ] Bold key phrases (sparingly)
- [ ] Table of contents for 2,000+ word content

**Media:**
- [ ] Images with descriptive alt text
- [ ] Image file names include keywords
- [ ] Images compressed for performance
- [ ] Videos embedded (increases time on page)

**Depth:**
- [ ] Answers the search query completely
- [ ] Covers related questions (PAA)
- [ ] More comprehensive than ranking competitors
- [ ] Updated with current information

### Image Optimization

| Element | Best Practice |
|---------|---------------|
| **Alt text** | Descriptive, includes keyword if natural |
| **File name** | keyword-description.png (not IMG_12345.png) |
| **Format** | WebP preferred, PNG for graphics, JPG for photos |
| **Size** | Compress to <100KB when possible |
| **Dimensions** | Specify width/height to prevent layout shift |

### Good Alt Text

```html
✓ <img src="kubernetes-secrets-architecture.png"
       alt="Diagram showing Kubernetes secrets flow from external secrets manager to pod">

✓ <img src="vault-dashboard.png"
       alt="HashiCorp Vault dashboard showing secret engine configuration">
```

### Bad Alt Text

```html
✗ <img alt="">
  (Missing alt text)

✗ <img alt="image">
  (Non-descriptive)

✗ <img alt="kubernetes secrets secret management k8s secrets docker secrets vault aws">
  (Keyword stuffing)
```

### Content Freshness Signals

| Signal | How to Implement |
|--------|------------------|
| **Publish date** | Display and keep current |
| **Last updated** | Show when content refreshed |
| **Year in title** | "Guide (2024)" for evergreen |
| **Current statistics** | Update annually at minimum |
| **Working examples** | Test code samples regularly |

### Anti-Patterns

- **Title/H1 mismatch** — Confuses both users and Google
- **Keyword stuffing** — Hurts readability, triggers spam filters
- **Thin content** — <300 words rarely ranks for competitive terms
- **Missing meta descriptions** — Leaves SERP snippet to chance
- **Duplicate title tags** — Every page competes with itself
- **Walls of text** — No formatting kills engagement
- **Hidden text** — Any technique to hide keywords is spam
- **Over-optimization** — Keyword in every H2 looks unnatural
- **Ignoring mobile** — 60%+ traffic is mobile; optimize for it
