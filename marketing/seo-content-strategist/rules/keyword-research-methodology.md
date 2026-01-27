---
title: Keyword Research Methodology
impact: CRITICAL
tags: keywords, research, topics, search-volume, difficulty
---

## Keyword Research Methodology

**Impact: CRITICAL**

Keyword research is the foundation of SEO strategy. Target the wrong keywords and everything downstream fails — great content that nobody searches for, or high-volume terms you'll never rank for.

### Keyword Research Process

```
1. Seed Keywords
   └── Start with 5-10 core terms your business owns

2. Expansion
   └── Tools, competitors, related searches, questions

3. Classification
   └── Intent, funnel stage, topic cluster

4. Prioritization
   └── Volume × Intent × Achievability

5. Mapping
   └── Assign keywords to content pieces
```

### Keyword Metrics That Matter

| Metric | What It Means | How to Use |
|--------|---------------|------------|
| **Search Volume** | Monthly searches | Ceiling for traffic potential |
| **Keyword Difficulty** | Competition level (0-100) | Realistic ranking potential |
| **CPC** | What advertisers pay | Proxy for commercial value |
| **Click Potential** | % of searches that click | Beware zero-click queries |
| **Trend** | Volume direction | Growing > declining keywords |
| **SERP Features** | What appears in results | Affects CTR and strategy |

### Keyword Difficulty Guidelines

| Difficulty Score | Site Requirement | Timeline |
|------------------|------------------|----------|
| **0-20** | New sites can rank | 1-3 months |
| **21-40** | Some authority needed | 3-6 months |
| **41-60** | Established domain | 6-12 months |
| **61-80** | Strong authority | 12-18 months |
| **81-100** | Major brand/site | 18+ months or avoid |

### Seed Keyword Sources

| Source | Example | Best For |
|--------|---------|----------|
| **Product features** | "API key rotation" | Product-led content |
| **Customer problems** | "how to prevent data breaches" | Problem-aware audience |
| **Competitor analysis** | Terms competitors rank for | Gap identification |
| **Sales conversations** | What prospects ask about | High-intent terms |
| **Support tickets** | Common questions | FAQ and help content |
| **Industry terms** | "secrets management" | Category content |

### Good Keyword Research

```
✓ Primary keyword: "kubernetes secrets management"
  └── Volume: 1,200/mo
  └── Difficulty: 35
  └── Intent: Commercial investigation
  └── CPC: $15 (high commercial value)
  └── SERP analysis: Mix of how-tos and comparisons
  └── Opportunity: No clear winner, guides are outdated

✓ Secondary keywords (same page):
  └── "k8s secrets best practices" (480/mo)
  └── "kubernetes secret management tools" (320/mo)
  └── "how to manage secrets in kubernetes" (260/mo)

✓ Related questions to answer:
  └── "Should you store secrets in kubernetes?"
  └── "What is the best way to manage kubernetes secrets?"
  └── "Kubernetes secrets vs external secrets"
```

### Bad Keyword Research

```
✗ Target: "security"
  └── Volume: 1,000,000/mo
  └── Difficulty: 95
  └── Problem: Way too broad, unrankaeable, unclear intent

✗ Target: "infisical vs competitor nobody knows"
  └── Volume: 10/mo
  └── Problem: No search demand exists

✗ Target: "buy secrets management software now"
  └── Volume: 0/mo
  └── Problem: Not how people search

✗ Targeting only head terms:
  └── "secrets management" but not
  └── "secrets management for startups" or
  └── "secrets management best practices" or
  └── "secrets management tools comparison"
```

### Keyword Intent Classification

| Signal | Informational | Commercial | Transactional |
|--------|---------------|------------|---------------|
| **Modifiers** | how, what, why, guide | best, top, vs, review | buy, pricing, demo, trial |
| **SERP type** | Blog posts, wikis | Listicles, comparisons | Product pages, pricing |
| **User stage** | Awareness | Consideration | Decision |
| **Content fit** | Educational | Evaluative | Conversion |

### Keyword Opportunity Score

Calculate: `(Volume × Intent Score × Click Rate) / Difficulty`

| Factor | Scoring |
|--------|---------|
| **Volume** | Raw number |
| **Intent Score** | Info=1, Commercial=3, Transactional=5 |
| **Click Rate** | % of SERPs with organic clicks (check for zero-click) |
| **Difficulty** | 1-100 from tool |

Higher score = better opportunity.

### Long-Tail Strategy

| Term Type | Example | Characteristics |
|-----------|---------|-----------------|
| **Head** | "secrets management" | High volume, high difficulty, broad intent |
| **Body** | "secrets management for startups" | Medium volume, medium difficulty |
| **Long-tail** | "how to rotate api keys in kubernetes" | Low volume, low difficulty, specific intent |

**Long-tail advantages:**
- Easier to rank
- Higher conversion rate
- More specific content
- Builds topical authority for head terms

### Competitor Keyword Gap Analysis

```
1. Identify 3-5 direct competitors

2. Export their ranking keywords

3. Filter to:
   └── Keywords you DON'T rank for
   └── Keywords where they rank higher
   └── Keywords with volume > 100/mo

4. Categorize gaps:
   └── Missing topics (need new content)
   └── Weak coverage (need better content)
   └── Technical issues (need optimization)

5. Prioritize by opportunity score
```

### Question Keyword Mining

| Source | How to Access |
|--------|---------------|
| **People Also Ask** | Google SERP → expand PAA boxes |
| **Related Searches** | Bottom of Google SERP |
| **Answer the Public** | answerthepublic.com |
| **AlsoAsked** | alsoasked.com |
| **Reddit/Quora** | Search `site:reddit.com [topic]` |
| **Customer calls** | Record and transcribe sales/support calls |

### Keyword Research Checklist

- [ ] Identified 5-10 seed keywords from product/customer research
- [ ] Expanded to 100+ keyword variations using tools
- [ ] Classified all keywords by intent
- [ ] Checked SERP for each primary keyword
- [ ] Identified keyword difficulty and realistic targets
- [ ] Grouped keywords into topic clusters
- [ ] Mapped keywords to funnel stages
- [ ] Found question keywords for each topic
- [ ] Analyzed competitor keyword gaps
- [ ] Prioritized by opportunity score
- [ ] Assigned keywords to content pieces

### Anti-Patterns

- **Volume obsession** — Chasing 50k/mo terms you'll never rank for
- **Ignoring intent** — Ranking #1 for wrong intent = 90% bounce rate
- **Keyword hoarding** — Researching 1,000 keywords, executing on 10
- **Tool over-reliance** — Tools estimate; SERP analysis confirms
- **Static research** — Search behavior changes; refresh quarterly
- **Skipping SERP analysis** — Difficulty score means nothing without checking actual results
- **One keyword per page** — Modern SEO targets topic clusters, not single keywords
- **Ignoring zero-click** — Some keywords have no click-through opportunity
