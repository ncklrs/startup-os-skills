---
title: Technical SEO for SaaS Sites
impact: HIGH
tags: technical-seo, site-architecture, crawlability, indexation, core-web-vitals, schema
---

## Technical SEO for SaaS Sites

**Impact: HIGH**

Technical SEO is the foundation that enables content to rank. A technically sound site with average content outperforms a technically broken site with excellent content. For SaaS, this includes specific challenges around app vs. marketing pages, JavaScript rendering, and documentation.

### Technical SEO Audit Checklist

```
Crawlability
├── [ ] Robots.txt configured correctly
├── [ ] XML sitemap submitted and updated
├── [ ] No critical pages blocked
├── [ ] Crawl budget not wasted on low-value pages
└── [ ] Internal linking enables discovery

Indexation
├── [ ] Target pages are indexed (site: search)
├── [ ] No unwanted pages indexed (filters, params)
├── [ ] Canonical tags implemented correctly
├── [ ] No duplicate content issues
└── [ ] Hreflang for international (if applicable)

Performance
├── [ ] Core Web Vitals passing
├── [ ] Mobile-friendly (responsive)
├── [ ] HTTPS enabled
├── [ ] Fast TTFB (<200ms)
└── [ ] Images optimized

Structure
├── [ ] Clear URL hierarchy
├── [ ] Breadcrumbs implemented
├── [ ] Schema markup on key pages
├── [ ] 404 page exists and is helpful
└── [ ] Redirects are 301 (not 302)
```

### Robots.txt for SaaS

```
# Good robots.txt for SaaS site

User-agent: *
Allow: /
Disallow: /app/
Disallow: /dashboard/
Disallow: /api/
Disallow: /admin/
Disallow: /*?*utm_
Disallow: /*?*ref=
Disallow: /search?

# Allow marketing/docs pages that might be under /app path
Allow: /app/signup
Allow: /app/login

Sitemap: https://example.com/sitemap.xml
```

### Bad Robots.txt Mistakes

```
✗ User-agent: *
  Disallow: /
  (Blocks entire site!)

✗ No robots.txt at all
  (Bots crawl everything, including app pages)

✗ Disallow: /blog
  (Blocking your main content!)

✗ Forgetting sitemap reference
  (Bots have to discover sitemap another way)
```

### XML Sitemap Best Practices

| Rule | Guideline |
|------|-----------|
| **Include** | All pages you want indexed |
| **Exclude** | Thin pages, duplicates, app pages |
| **Update** | Automatically when content changes |
| **Size** | Max 50,000 URLs or 50MB per sitemap |
| **Priority** | Homepage > main pages > blog posts |
| **Frequency** | Reflect actual update frequency |

### Core Web Vitals Targets

| Metric | What It Measures | Good | Needs Work | Poor |
|--------|------------------|------|------------|------|
| **LCP** | Largest Contentful Paint | <2.5s | 2.5-4s | >4s |
| **INP** | Interaction to Next Paint | <200ms | 200-500ms | >500ms |
| **CLS** | Cumulative Layout Shift | <0.1 | 0.1-0.25 | >0.25 |

### Common CWV Fixes for SaaS Sites

| Issue | Cause | Fix |
|-------|-------|-----|
| **Poor LCP** | Large hero images | Preload, compress, use WebP |
| **Poor LCP** | Slow server response | CDN, edge caching |
| **Poor LCP** | Render-blocking JS | Defer non-critical scripts |
| **Poor INP** | Heavy JavaScript | Code splitting, lazy loading |
| **Poor INP** | Third-party scripts | Delay analytics, chat widgets |
| **High CLS** | Images without dimensions | Set width/height attributes |
| **High CLS** | Dynamic content injection | Reserve space for ads/embeds |
| **High CLS** | Web fonts | font-display: swap, preload |

### JavaScript SEO for SaaS

```
Common issue: Marketing site uses same React/Next.js stack as app

Problems:
├── Content rendered client-side → not indexed
├── Slow initial load → poor CWV
├── Links not crawlable → poor internal linking
└── Dynamic routing → canonical issues

Solutions:
├── SSR (Server-Side Rendering) for marketing pages
├── SSG (Static Site Generation) for blog/docs
├── Prerendering service as fallback
├── Test with Google's URL Inspection Tool
└── Check "View Rendered Source" vs "View Source"
```

### Canonical Tag Implementation

| Scenario | Canonical Should Point To |
|----------|---------------------------|
| **Single URL, no variants** | Self-referencing canonical |
| **www vs non-www** | Preferred version |
| **HTTP vs HTTPS** | HTTPS version |
| **With/without trailing slash** | Chosen standard |
| **Paginated content** | Usually self-referencing |
| **Filtered/sorted versions** | Base URL (no parameters) |
| **Syndicated content** | Original source |

### Good Canonical Implementation

```html
<!-- On page: https://example.com/blog/secrets-management -->
<link rel="canonical" href="https://example.com/blog/secrets-management" />

<!-- On page: https://example.com/blog/secrets-management?utm_source=twitter -->
<link rel="canonical" href="https://example.com/blog/secrets-management" />

<!-- On filtered page: https://example.com/tools?category=secrets -->
<link rel="canonical" href="https://example.com/tools" />
```

### Bad Canonical Mistakes

```html
✗ Canonical to homepage from every page
  <link rel="canonical" href="https://example.com/" />
  (Tells Google all your pages are duplicates of homepage)

✗ Canonical pointing to 404 page
  (Page won't rank, confuses indexing)

✗ HTTP canonical on HTTPS page
  <link rel="canonical" href="http://example.com/page" />
  (Protocol mismatch)

✗ No canonical at all
  (Google guesses, often incorrectly)
```

### Site Architecture for SaaS

```
Good structure:
example.com/
├── / (homepage)
├── /product/
│   ├── /product/features/
│   ├── /product/security/
│   └── /product/integrations/
├── /solutions/
│   ├── /solutions/enterprise/
│   └── /solutions/startups/
├── /pricing/
├── /blog/
│   ├── /blog/[category]/
│   └── /blog/[post-slug]/
├── /docs/
│   ├── /docs/getting-started/
│   └── /docs/api-reference/
├── /customers/
└── /company/
    ├── /company/about/
    └── /company/careers/
```

### Schema Markup for SaaS

| Page Type | Schema Type | Key Properties |
|-----------|-------------|----------------|
| **Homepage** | Organization | name, logo, sameAs |
| **Product page** | SoftwareApplication | name, operatingSystem, offers |
| **Blog post** | Article | headline, author, datePublished |
| **FAQ page** | FAQPage | mainEntity (questions/answers) |
| **How-to** | HowTo | step, tool, supply |
| **Pricing** | Product + Offer | price, priceCurrency |
| **Documentation** | TechArticle | dependencies, proficiencyLevel |

### Good Schema for Blog Post

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Kubernetes Secrets Management Guide",
  "description": "Learn how to securely manage secrets in Kubernetes...",
  "author": {
    "@type": "Person",
    "name": "Jane Developer"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Infisical",
    "logo": {
      "@type": "ImageObject",
      "url": "https://infisical.com/logo.png"
    }
  },
  "datePublished": "2024-01-15",
  "dateModified": "2024-03-20"
}
```

### Redirect Best Practices

| Situation | Redirect Type | Notes |
|-----------|---------------|-------|
| **Permanent move** | 301 | Passes ~90% link equity |
| **Temporary move** | 302 | No link equity passed |
| **URL change** | 301 | Old URL → new URL |
| **Domain change** | 301 | Every old URL → equivalent new URL |
| **HTTP → HTTPS** | 301 | Required for HTTPS migration |
| **Deleted page** | 301 to relevant page | Don't 404 pages with backlinks |

### Common Redirect Mistakes

```
✗ Redirect chains:
  /old → /intermediate → /new
  (Should be: /old → /new)

✗ Redirect loops:
  /page-a → /page-b → /page-a
  (Infinite loop, page won't load)

✗ 302 for permanent changes:
  (Link equity not passed)

✗ Redirect to homepage for all deleted pages:
  /specific-topic → / (homepage)
  (Should redirect to most relevant page)
```

### Mobile Optimization

| Element | Requirement |
|---------|-------------|
| **Responsive design** | Single URL for mobile/desktop |
| **Tap targets** | Minimum 48px spacing |
| **Font size** | Minimum 16px base |
| **Viewport** | meta viewport tag set |
| **No horizontal scroll** | Content fits screen width |
| **Touch-friendly** | No hover-dependent features |

### Site Speed Tools

| Tool | What It Measures | When to Use |
|------|------------------|-------------|
| **PageSpeed Insights** | CWV, performance score | Individual page analysis |
| **Chrome DevTools** | Network, rendering, JS | Deep debugging |
| **WebPageTest** | Waterfall, filmstrip | Detailed load analysis |
| **GTmetrix** | Combined metrics | Quick overview |
| **Search Console** | CWV across site | Site-wide monitoring |
| **Lighthouse CI** | Automated testing | CI/CD integration |

### Anti-Patterns

- **Blocking JS/CSS in robots.txt** — Google can't render pages properly
- **Soft 404s** — Page returns 200 but shows "not found" content
- **Orphan pages** — No internal links pointing to page
- **Infinite scroll without pagination** — Bots can't access content
- **Faceted navigation mess** — Creates thousands of crawlable filter URLs
- **No HTTPS** — Ranking factor, user trust issue
- **Slow hosting** — >3s load time kills rankings and conversions
- **Mixed content** — HTTPS page loading HTTP resources
- **Missing alt tags on critical images** — Accessibility and SEO issue
- **App and marketing on same subdomain** — Confuses crawlers
