---
title: Events to Never Sample Away
impact: CRITICAL
tags: sampling, errors, retention
---

## Events to Never Sample Away

**Impact: CRITICAL**

Some events must have 100% retention regardless of volume or cost. Losing these during an outage is unacceptable.

### Always Keep Categories

| Category | Criteria | Why |
|----------|----------|-----|
| **Errors** | `outcome = failure` OR `status >= 500` | Every error is signal |
| **Slow Requests** | `duration_ms > p99_threshold` | Performance issues affect UX |
| **VIP Customers** | Enterprise tier, high LTV | Business-critical users |
| **New Users** | `account_age < 7 days` | Onboarding issues |
| **Feature Flags** | Any request with active experiments | Rollout debugging |
| **High Value** | Transactions > threshold | Revenue impact |
| **Security Events** | Auth failures, permission denials | Security monitoring |
| **Rate Limited** | Requests that hit limits | Capacity planning |

### Implementation

```typescript
const ALWAYS_KEEP_RULES: SamplingRule[] = [
  // === ERRORS ===
  {
    name: 'server_errors',
    condition: (e) => e.status_code >= 500,
    reason: 'Server errors must always be retained'
  },
  {
    name: 'client_errors_auth',
    condition: (e) => e.status_code === 401 || e.status_code === 403,
    reason: 'Auth failures are security-relevant'
  },
  {
    name: 'outcome_failure',
    condition: (e) => e.outcome === 'failure',
    reason: 'All business failures are signal'
  },

  // === PERFORMANCE ===
  {
    name: 'slow_requests',
    condition: (e) => e.duration_ms > getP99(e.path) * 1.5,
    reason: 'Slow requests indicate degradation'
  },
  {
    name: 'timeout',
    condition: (e) => e.error?.type === 'TIMEOUT',
    reason: 'Timeouts indicate system issues'
  },

  // === BUSINESS CRITICAL ===
  {
    name: 'vip_customers',
    condition: (e) => e.user?.tier === 'enterprise' || e.user?.is_vip,
    reason: 'Enterprise customers expect reliability'
  },
  {
    name: 'high_value_transactions',
    condition: (e) => (e.transaction?.amount_cents ?? 0) > 100000,
    reason: 'High-value transactions are revenue-critical'
  },
  {
    name: 'new_users',
    condition: (e) => (e.user?.account_age_days ?? Infinity) < 7,
    reason: 'New user experience is critical for retention'
  },

  // === DEBUGGING ===
  {
    name: 'feature_flagged',
    condition: (e) => (e.feature_flags?.length ?? 0) > 0,
    reason: 'Need full visibility during rollouts'
  },
  {
    name: 'canary_deployment',
    condition: (e) => e.deployment_ring === 'canary',
    reason: 'Canary deployments need 100% observability'
  },

  // === SECURITY ===
  {
    name: 'rate_limited',
    condition: (e) => e.is_rate_limited,
    reason: 'Rate limiting indicates abuse or capacity issues'
  },
  {
    name: 'suspicious_activity',
    condition: (e) => e.security?.risk_score > 0.7,
    reason: 'Security events require full audit trail'
  }
];

function mustKeep(event: WideEvent): { keep: boolean; reason?: string } {
  for (const rule of ALWAYS_KEEP_RULES) {
    if (rule.condition(event)) {
      return { keep: true, reason: rule.name };
    }
  }
  return { keep: false };
}
```

### Cost Management

If always-keep volume becomes expensive:

1. **Aggregate, don't drop**: Keep 100% of error metadata, sample error details
2. **Tiered storage**: Move old always-keep events to cold storage
3. **Fix the cause**: High error volume = fix bugs, don't hide them

### Bad Example: Dropping Errors

```javascript
// ❌ NEVER DO THIS
if (Math.random() > 0.05) {
  return; // Might drop critical error!
}
logger.error(event);
```

### Checklist

- [ ] All 5XX errors retained at 100%
- [ ] All auth failures (401/403) retained
- [ ] Slow requests above p99 retained
- [ ] VIP/enterprise customer requests retained
- [ ] Feature-flagged requests retained
- [ ] New user requests retained
- [ ] High-value transactions retained
- [ ] Security-relevant events retained
