---
title: Required Context Fields
impact: HIGH
tags: fields, context, standard-fields
---

## Required Context Fields

**Impact: HIGH**

Every wide event must include baseline context fields. These enable filtering, correlation, and debugging across your entire system.

### Minimum Required Fields

```typescript
interface RequiredEventFields {
  // Identity
  request_id: string;      // Unique per request
  trace_id?: string;       // Distributed tracing correlation

  // Timing
  timestamp: number;       // Unix epoch ms
  duration_ms: number;     // Request duration

  // Service metadata
  service: string;         // Service name
  version: string;         // Deployment version
  environment: string;     // prod/staging/dev
  region: string;          // Deployment region
  instance_id: string;     // Container/instance ID

  // Request details
  method: string;          // HTTP method or RPC name
  path: string;            // Endpoint path
  status_code: number;     // Response status

  // Outcome
  outcome: 'success' | 'failure';
}
```

### Good Example: Complete Context

```javascript
const event = {
  // === IDENTITY ===
  request_id: crypto.randomUUID(),
  trace_id: req.headers['x-trace-id'],
  span_id: crypto.randomUUID(),
  parent_span_id: req.headers['x-parent-span-id'],

  // === TIMING ===
  timestamp: Date.now(),
  duration_ms: 0, // Set at completion

  // === SERVICE METADATA ===
  service: "checkout-api",
  version: "2.3.1",
  git_sha: "abc123f",
  environment: "production",
  region: "us-east-1",
  availability_zone: "us-east-1a",
  instance_id: "i-0123456789",
  kubernetes_pod: "checkout-api-7f8d9-xk2lm",

  // === REQUEST ===
  method: "POST",
  path: "/v1/checkout",
  route_pattern: "/v1/checkout", // Normalized (no IDs)
  query_params: { expand: "items" },
  content_length: 1247,
  user_agent: req.headers['user-agent'],
  client_ip: req.ip, // Or anonymized

  // === RESPONSE ===
  status_code: 200,
  response_size_bytes: 892,

  // === OUTCOME ===
  outcome: "success"
};
```

### Deployment Context (Often Missed)

```javascript
// Capture at service startup, include in every event
const deploymentContext = {
  version: process.env.SERVICE_VERSION,
  git_sha: process.env.GIT_SHA,
  deploy_id: process.env.DEPLOY_ID,
  deployed_at: process.env.DEPLOY_TIMESTAMP,
  deployed_by: process.env.DEPLOY_USER,

  // Kubernetes context
  kubernetes_namespace: process.env.K8S_NAMESPACE,
  kubernetes_pod: process.env.K8S_POD_NAME,
  kubernetes_node: process.env.K8S_NODE_NAME,

  // Feature flags snapshot
  feature_flags: getActiveFlags()
};

// Merge into every event
const event = {
  ...deploymentContext,
  ...requestContext
};
```

### Bad Example: Missing Critical Context

```javascript
// ❌ Can't correlate, can't identify which version, can't filter by region
const event = {
  message: "checkout completed",
  userId: "123"
};
```

### Context Categories

| Category | Fields | Purpose |
|----------|--------|---------|
| **Identity** | request_id, trace_id, span_id | Correlation |
| **Timing** | timestamp, duration_ms | Performance |
| **Service** | service, version, region, instance | Isolation |
| **Request** | method, path, status | API debugging |
| **Deployment** | git_sha, deploy_id, feature_flags | Rollback analysis |

### Checklist

- [ ] Every event has request_id and timestamp
- [ ] Service name, version, and region are included
- [ ] Deployment metadata (git SHA, deploy ID) captured
- [ ] Request method, path, and status code present
- [ ] Duration calculated and included
- [ ] Clear success/failure outcome field
