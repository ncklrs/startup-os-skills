---
title: Changelog Entry Writing
impact: CRITICAL
tags: changelog, release-notes, user-communication
---

## Changelog Entry Writing

**Impact: CRITICAL**

Changelog entries are user-facing communication. Write for the person using your software, not the person who wrote it.

### Entry Formula

```
<Action verb> <what changed> <benefit/context> (<reference>)
```

### Good Entries

```markdown
### Added
- Add dark mode toggle in settings (#234)
- Add CSV export for reports, supporting up to 100k rows (#567)
- Add keyboard shortcuts for common actions (see docs) (#789)

### Changed
- Improve dashboard load time by 40% through query optimization (#345)
- Update authentication to support SSO providers (#456)
- Replace date picker with more accessible component (#678)

### Fixed
- Fix crash when uploading files larger than 10MB (#123)
- Fix incorrect timezone display for users outside UTC (#234)
- Fix memory leak in real-time notifications (#345)

### Security
- Fix XSS vulnerability in comment rendering (CVE-2024-1234)
- Upgrade dependencies to patch known vulnerabilities
```

### Bad Entries

```markdown
✗ "Fixed bug"
  → What bug? What was the impact?

✗ "Refactored authentication module"
  → User doesn't care about refactoring unless behavior changed

✗ "Updated dependencies"
  → Only mention if it affects users (security, breaking changes)

✗ "WIP: Started working on new feature"
  → Changelog is for completed changes only

✗ "Merge pull request #123 from feature-branch"
  → Copy-pasted from git log, provides no context
```

### Writing Guidelines

1. **Start with a verb** — Add, Fix, Remove, Update, Improve
2. **Be specific** — "Fix crash on iOS 17" not "Fix mobile bug"
3. **Include impact** — "40% faster" beats "improved performance"
4. **Reference issues/PRs** — Traceability for curious users
5. **Group related changes** — One entry for multiple related fixes

### Verb Choices

| Action | Good Verbs |
|--------|-----------|
| New feature | Add, Introduce, Support |
| Modification | Update, Improve, Enhance, Optimize |
| Bug fix | Fix, Resolve, Correct |
| Removal | Remove, Drop, Delete |
| Deprecation | Deprecate, Mark as deprecated |

### Length Guidelines

- **One-liner** — Most entries (80% of changelog)
- **Short paragraph** — Breaking changes, major features
- **With sub-bullets** — Complex features with multiple aspects

### What NOT to Include

- Internal refactoring (unless it improves performance)
- Test additions/changes
- CI/CD pipeline changes
- Documentation-only changes (unless user-facing)
- Dependency bumps (unless security-related)

### Checklist

- [ ] Written from user's perspective
- [ ] Starts with action verb
- [ ] Includes PR/issue reference
- [ ] Categorized correctly (Added/Changed/Fixed/etc.)
- [ ] No jargon or internal terminology
