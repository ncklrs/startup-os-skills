---
title: Wiki Page Structure
impact: HIGH
tags: wiki, documentation, structure, organization
---

## Wiki Page Structure

**Impact: HIGH**

Well-structured wiki pages help users find information quickly and understand context.

### Page Template

```markdown
# Page Title

Brief description of what this page covers (1-2 sentences).

## Overview

Expanded context. Why does this exist? Who is it for?

## Prerequisites

What users need before following this guide:
- Required knowledge
- Required tools/access
- Links to prerequisite pages

## Main Content

### Section 1
Content...

### Section 2
Content...

## Examples

Practical examples with code blocks.

## Troubleshooting

Common issues and solutions.

## Related Pages

- [Related Topic 1](Related-Topic-1)
- [Related Topic 2](Related-Topic-2)

## See Also

- [External resource](https://example.com)
```

### Good Page Structure

```markdown
# Authentication

Set up authentication for your application using OAuth 2.0 or API keys.

## Overview

Our API supports two authentication methods:
- **OAuth 2.0** — For user-facing applications
- **API Keys** — For server-to-server communication

## Prerequisites

- An active account ([Sign up](https://example.com/signup))
- Basic understanding of HTTP headers

## OAuth 2.0 Setup

### Step 1: Create an OAuth App

1. Go to Settings → Developer → OAuth Apps
2. Click "New OAuth App"
3. Fill in the required fields:
   - **Name**: Your app name
   - **Redirect URI**: `https://yourapp.com/callback`

### Step 2: Implement the Flow

\`\`\`javascript
const authUrl = `https://api.example.com/oauth/authorize?
  client_id=${CLIENT_ID}&
  redirect_uri=${REDIRECT_URI}&
  scope=read,write`;
\`\`\`

## API Key Authentication

For server-to-server communication...

## Troubleshooting

### "Invalid token" error

This usually means your token has expired. Tokens expire after 24 hours.
[Refresh your token](Token-Refresh) to resolve.

### "Scope insufficient" error

Your token doesn't have the required permissions...

## Related Pages

- [Token Refresh](Token-Refresh)
- [Rate Limiting](Rate-Limiting)
- [Error Codes](Error-Codes)
```

### Bad Page Structure

```markdown
✗ No overview
# Authentication
Here's how to authenticate...
(User doesn't know what methods are available)

✗ Wall of text
# Setup Guide
First you need to download the CLI then you need to run npm install
then you need to configure the environment variables which are listed
below and then you can run the server...
(No structure, hard to scan)

✗ Missing prerequisites
# Advanced Configuration
Modify the `config.yaml` file...
(User doesn't know where this file is or what format to use)

✗ Dead-end page
# API Reference
(No links to related pages or next steps)
```

### Heading Hierarchy

```markdown
# Page Title (H1) — One per page
## Major Section (H2) — Primary divisions
### Subsection (H3) — Within major sections
#### Detail (H4) — Rarely needed, consider restructuring
```

### Content Guidelines

1. **Scannable** — Use headings, lists, and bold for key terms
2. **Progressive** — Start simple, add complexity
3. **Self-contained** — Each page should make sense alone
4. **Linked** — Connect to related pages liberally
5. **Actionable** — Tell users what to do, not just what exists

### Checklist

- [ ] Clear, descriptive title
- [ ] Brief intro explaining page purpose
- [ ] Prerequisites listed (if any)
- [ ] Logical heading hierarchy
- [ ] Code examples where applicable
- [ ] Related pages linked
- [ ] Troubleshooting section for guides
