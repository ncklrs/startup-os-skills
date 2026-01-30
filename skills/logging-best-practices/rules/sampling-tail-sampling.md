---
title: Tail Sampling Strategy
impact: HIGH
tags: sampling, cost, observability
---

## Tail Sampling Strategy

**Impact: HIGH**

Make sampling decisions **after request completion** based on outcomes. This ensures you keep 100% of important events (errors, slow requests, VIPs) while sampling routine traffic.

### Head vs Tail Sampling

| Strategy | When Decision Made | Problem |
|----------|-------------------|---------|
| **Head Sampling** | Request start | Drops errors randomly—you might sample away critical failures |
| **Tail Sampling** | Request completion | Keeps all important events, samples the rest |

### Tail Sampling Decision Logic

```typescript
interface SamplingDecision {
  keep: boolean;
  reason: string;
  sample_rate: number;  // For weighted analytics
}

function shouldKeepEvent(event: WideEvent): SamplingDecision {
  // === ALWAYS KEEP (100% retention) ===

  // All errors
  if (event.outcome === 'failure' || event.status_code >= 500) {
    return { keep: true, reason: 'error', sample_rate: 1.0 };
  }

  // Slow requests (above p99)
  if (event.duration_ms > getP99Threshold(event.path)) {
    return { keep: true, reason: 'slow', sample_rate: 1.0 };
  }

  // VIP customers
  if (event.user?.tier === 'enterprise' || event.user?.is_vip) {
    return { keep: true, reason: 'vip', sample_rate: 1.0 };
  }

  // Feature-flagged requests (rollout debugging)
  if (event.feature_flags?.includes('new_checkout_v2')) {
    return { keep: true, reason: 'feature_flag', sample_rate: 1.0 };
  }

  // Recent signups (onboarding issues)
  if (event.user?.account_age_days < 7) {
    return { keep: true, reason: 'new_user', sample_rate: 1.0 };
  }

  // High-value transactions
  if (event.transaction?.amount_cents > 100000) { // > $1000
    return { keep: true, reason: 'high_value', sample_rate: 1.0 };
  }

  // === SAMPLE THE REST ===

  // 5% of successful, fast, routine requests
  const shouldSample = Math.random() < 0.05;
  return {
    keep: shouldSample,
    reason: 'random_sample',
    sample_rate: 0.05
  };
}
```

### Implementation Pattern

```typescript
// Final middleware applies sampling
app.use((req, res, next) => {
  res.on('finish', () => {
    const event = finalizeEvent(res.statusCode < 400 ? 'success' : 'failure');
    const decision = shouldKeepEvent(event);

    if (decision.keep) {
      // Include sample_rate for weighted analytics
      event._sampling = {
        kept: true,
        reason: decision.reason,
        rate: decision.sample_rate
      };
      logger.info(event);
    }
  });
  next();
});
```

### Weighted Analytics

When analyzing sampled data, weight by inverse sample rate:

```sql
-- Correct: Weight sampled events
SELECT
  path,
  SUM(1 / _sampling.rate) as estimated_total_requests,
  COUNT(*) as sampled_count
FROM logs
WHERE timestamp > NOW() - INTERVAL 1 HOUR
GROUP BY path;

-- Wrong: Raw counts underrepresent sampled traffic
SELECT path, COUNT(*) FROM logs GROUP BY path; -- Misleading!
```

### Bad Example: Head Sampling

```javascript
// ❌ Decision at request START — might drop errors
app.use((req, res, next) => {
  // 5% random sample before we know if this will fail
  if (Math.random() > 0.05) {
    req.skipLogging = true;  // Might skip a critical error!
  }
  next();
});
```

### Checklist

- [ ] Sampling decision made after request completion
- [ ] 100% retention for errors and 5XX responses
- [ ] 100% retention for slow requests (above p99)
- [ ] 100% retention for VIP/enterprise customers
- [ ] 100% retention for feature-flagged requests
- [ ] Sample rate included in event for weighted analytics
- [ ] 1-10% sampling for routine successful requests
