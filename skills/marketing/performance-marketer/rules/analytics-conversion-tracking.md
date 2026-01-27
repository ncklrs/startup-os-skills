---
title: Conversion Tracking
impact: HIGH
tags: conversion-tracking, pixels, analytics, measurement
---

## Conversion Tracking

**Impact: HIGH**

Without accurate conversion tracking, you're flying blind. Every optimization decision depends on reliable data.

### Tracking Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    USER BROWSER                         │
│  ┌───────────────────────────────────────────────────┐  │
│  │  Client-Side Tracking                             │  │
│  │  • Google Analytics (gtag.js)                     │  │
│  │  • Meta Pixel (fbq)                               │  │
│  │  • LinkedIn Insight Tag                           │  │
│  │  • GTM (Google Tag Manager)                       │  │
│  └───────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────┐
│                    YOUR SERVER                          │
│  ┌───────────────────────────────────────────────────┐  │
│  │  Server-Side Tracking (CAPI)                      │  │
│  │  • Meta Conversions API                           │  │
│  │  • Google Enhanced Conversions                    │  │
│  │  • LinkedIn Conversions API                       │  │
│  │  • Server-side GTM                                │  │
│  └───────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────┘
```

### Conversion Events Hierarchy

| Event Type | Examples | Priority |
|------------|----------|----------|
| **Primary** | Purchase, Signup, Demo booked | Track first |
| **Secondary** | Add to cart, Lead form, Trial start | High value |
| **Micro** | Pricing page, Feature page, Video watch | Engagement |
| **Engagement** | Page view, Scroll, Time on site | Optimization |

### Standard Events by Platform

| Event | Google | Meta | LinkedIn |
|-------|--------|------|----------|
| Page view | page_view | PageView | page_view |
| Sign up | sign_up | CompleteRegistration | conversion |
| Lead | generate_lead | Lead | conversion |
| Purchase | purchase | Purchase | conversion |
| Add to cart | add_to_cart | AddToCart | - |
| Begin checkout | begin_checkout | InitiateCheckout | - |
| View content | view_item | ViewContent | - |
| Search | search | Search | - |

### Event Parameters

Include with every conversion:

```javascript
// Google Analytics 4
gtag('event', 'purchase', {
  transaction_id: 'T12345',
  value: 99.00,
  currency: 'USD',
  items: [{
    item_id: 'SKU123',
    item_name: 'Pro Plan Annual'
  }]
});

// Meta Pixel
fbq('track', 'Purchase', {
  value: 99.00,
  currency: 'USD',
  content_ids: ['SKU123'],
  content_type: 'product'
});
```

### Conversion Value Assignment

| Conversion Type | Value Approach | Example |
|-----------------|----------------|---------|
| **E-commerce** | Transaction value | $99.00 |
| **SaaS signup** | Expected LTV or first-year value | $500 |
| **Lead form** | Lead value × close rate | $50 |
| **Demo request** | Pipeline value × close rate | $200 |
| **Content download** | Estimated lead value | $20 |

### Tracking Verification Checklist

- [ ] Pixels loading on all pages
- [ ] Events firing correctly (test with extensions)
- [ ] Conversion values passing accurately
- [ ] Parameters populated (content_id, currency, etc.)
- [ ] Cross-domain tracking working
- [ ] Server-side tracking matching client-side
- [ ] Deduplication in place
- [ ] Test mode events showing in platforms

### Debug Tools

| Platform | Tool |
|----------|------|
| **Google** | Google Tag Assistant, GA4 DebugView |
| **Meta** | Meta Pixel Helper, Events Manager Test Events |
| **LinkedIn** | Insight Tag Helper, Conversions Test |
| **General** | Browser DevTools Network tab, GTM Preview |

### Good Tracking Implementation

```
✓ Enhanced conversion matching
  → User email hashed and sent server-side
  → Recovers 15-25% of missed conversions

✓ Primary + secondary events
  → Purchase as primary optimization event
  → Add-to-cart for funnel visibility

✓ Conversion value with margin
  → Revenue × margin passed as value
  → Enables ROAS optimization

✓ Server-side + client-side
  → Redundancy for accuracy
  → Deduplication by event_id
```

### Bad Tracking Implementation

```
✗ Thank you page only tracking
  → Misses users who close before page loads

✗ No conversion value
  → Algorithm can't optimize for ROAS

✗ Client-side only
  → Ad blockers hide 20-40% of conversions

✗ No test environment separation
  → Test conversions pollute real data

✗ Missing parameters
  → Can't analyze by content, product, etc.
```

### Server-Side Tracking (CAPI)

Why server-side matters:
- Ad blockers block client-side (20-40% traffic)
- iOS ATT reduces client-side accuracy
- Better data quality and consistency
- Required for some advanced features

| Platform | Implementation |
|----------|----------------|
| **Meta CAPI** | Event deduplication via event_id, hashed user data |
| **Google Enhanced** | Conversion tagging with user-provided data |
| **LinkedIn CAPI** | Server events with click ID matching |

### Deduplication

When using client-side + server-side, dedupe:

```javascript
// Generate unique event ID
const event_id = crypto.randomUUID();

// Client-side (Meta)
fbq('track', 'Purchase', {value: 99}, {eventID: event_id});

// Server-side (send same event_id)
// Meta will deduplicate based on event_id
```

### Cross-Domain Tracking

For sites spanning multiple domains:

| Platform | Method |
|----------|--------|
| **GA4** | Cross-domain configuration in GTM/settings |
| **Meta** | Automatic with same pixel ID |
| **GTM** | Link domains in tags, enable linker |

### Offline Conversions

For B2B or phone sales:

```
1. Capture click ID (gclid, fbclid, li_fat_id)
2. Store with lead record in CRM
3. When lead converts offline, upload to platform
4. Match via click ID or hashed email
```

### Privacy Compliance

| Requirement | Implementation |
|-------------|----------------|
| **GDPR** | Cookie consent before tracking |
| **CCPA** | Honor Do Not Sell signals |
| **iOS ATT** | Server-side tracking, consent prompts |
| **Cookie deprecation** | First-party data, server-side |

### Consent Mode (Google)

```javascript
// Default: denied
gtag('consent', 'default', {
  'ad_storage': 'denied',
  'analytics_storage': 'denied'
});

// After consent
gtag('consent', 'update', {
  'ad_storage': 'granted',
  'analytics_storage': 'granted'
});
```

### Tracking Audit Checklist

Monthly:
- [ ] Verify all pixels firing
- [ ] Check conversion counts match CRM
- [ ] Review server-side event delivery rate
- [ ] Audit UTM parameter consistency
- [ ] Test new pages and flows
- [ ] Check for tracking gaps in funnel

### Anti-Patterns

- **No server-side tracking** — Missing 20-40% of conversions
- **Duplicate conversions** — Inflates numbers, breaks optimization
- **Wrong conversion windows** — 7-day vs 28-day changes attribution
- **No value tracking** — Can't optimize for ROAS
- **Ignoring consent** — Legal risk, compliance issues
- **Set and forget** — Site changes break tracking
- **Test conversions in production** — Pollutes data
