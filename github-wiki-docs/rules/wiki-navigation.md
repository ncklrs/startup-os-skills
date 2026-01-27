---
title: Wiki Navigation
impact: HIGH
tags: wiki, navigation, sidebar, organization
---

## Wiki Navigation

**Impact: HIGH**

Good navigation helps users find content and understand how topics relate. The sidebar is your wiki's table of contents.

### Sidebar Structure (_Sidebar.md)

```markdown
**Getting Started**
- [Home](Home)
- [Quick Start](Quick-Start)
- [Installation](Installation)

**Guides**
- [Authentication](Authentication)
- [Configuration](Configuration)
- [Deployment](Deployment)

**API Reference**
- [REST API](REST-API)
- [GraphQL API](GraphQL-API)
- [Webhooks](Webhooks)

**Resources**
- [FAQ](FAQ)
- [Troubleshooting](Troubleshooting)
- [Changelog](Changelog)
```

### Good Navigation

```markdown
**🚀 Getting Started**
- [Home](Home)
- [Quick Start](Quick-Start) ← 5 min
- [Installation](Installation)
- [First Project](First-Project)

**📖 Core Concepts**
- [Architecture](Architecture)
- [Data Model](Data-Model)
- [Permissions](Permissions)

**🔧 Configuration**
- [Environment Variables](Environment-Variables)
- [Config Files](Config-Files)
- [Feature Flags](Feature-Flags)

**🔌 Integrations**
- [GitHub](Integration-GitHub)
- [Slack](Integration-Slack)
- [Jira](Integration-Jira)

**📚 Reference**
- [API Reference](API-Reference)
- [CLI Reference](CLI-Reference)
- [Error Codes](Error-Codes)

**❓ Help**
- [FAQ](FAQ)
- [Troubleshooting](Troubleshooting)
- [Support](Support)
```

### Bad Navigation

```markdown
✗ Flat list (no grouping)
- Home
- API
- Setup
- Config
- FAQ
- Installation
- Errors
(Hard to find what you need)

✗ Too deep (nested sub-lists)
- Getting Started
  - Installation
    - Mac
      - Homebrew
      - Manual
    - Windows
      - Chocolatey
      - Manual
(Sidebar becomes unwieldy)

✗ Inconsistent naming
- Home
- getting-started
- API Reference
- the_config_page
(Mix of cases and formats)
```

### Navigation Patterns

| Pattern | When to Use |
|---------|-------------|
| **Task-based** | "How do I..." — Group by user goals |
| **Topic-based** | "What is..." — Group by concepts |
| **Role-based** | Different content for devs vs admins |
| **Chronological** | Tutorials, getting started flows |

### Footer (_Footer.md)

Use footer for persistent links:

```markdown
---
[Report an Issue](https://github.com/owner/repo/issues) |
[Contribute](Contributing) |
[Changelog](Changelog)
```

### Cross-Linking Best Practices

1. **Link on first mention** — `[OAuth](Authentication#oauth-20)` when discussing auth
2. **Use descriptive text** — "See the [configuration guide](Configuration)" not "click [here](Configuration)"
3. **Link to sections** — `[Page-Name#section-heading](Page-Name#section-heading)`
4. **Add "See also" sections** — Related pages at the bottom

### Page Naming for URLs

| Page Name | URL |
|-----------|-----|
| `Home.md` | `/wiki/Home` |
| `Getting-Started.md` | `/wiki/Getting-Started` |
| `API-Reference.md` | `/wiki/API-Reference` |

Rules:
- Use hyphens (not spaces or underscores)
- PascalCase or kebab-case consistently
- Keep URLs readable and guessable

### Checklist

- [ ] Sidebar exists (`_Sidebar.md`)
- [ ] Pages grouped logically
- [ ] Section headers use bold or emoji
- [ ] Important pages easily accessible
- [ ] Consistent naming convention
- [ ] No orphan pages (all pages linked somewhere)
- [ ] Footer with essential links
