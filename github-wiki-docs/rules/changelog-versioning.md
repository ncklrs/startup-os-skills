---
title: Changelog Versioning
impact: CRITICAL
tags: changelog, semver, versioning, releases
---

## Changelog Versioning

**Impact: CRITICAL**

Version numbers communicate the nature of changes. Follow Semantic Versioning (SemVer) to set correct expectations.

### Semantic Versioning

```
MAJOR.MINOR.PATCH (e.g., 2.1.3)
```

| Component | When to Increment | Example |
|-----------|-------------------|---------|
| **MAJOR** | Breaking changes | API change, removed feature |
| **MINOR** | New features (backwards compatible) | New endpoint, new option |
| **PATCH** | Bug fixes (backwards compatible) | Fix crash, correct typo |

### Version Header Format

```markdown
## [1.2.3] - 2024-01-15
```

Components:
- Brackets around version number
- ISO 8601 date (YYYY-MM-DD)
- Hyphen separator
- No "v" prefix in changelog (but use in git tags)

### Unreleased Section

Always maintain an `[Unreleased]` section at the top:

```markdown
## [Unreleased]

### Added
- Work in progress feature

## [1.2.0] - 2024-01-15
...
```

When releasing, rename `[Unreleased]` to the new version and create fresh `[Unreleased]`.

### Link References

At the bottom of CHANGELOG.md, add comparison links:

```markdown
[Unreleased]: https://github.com/owner/repo/compare/v1.2.0...HEAD
[1.2.0]: https://github.com/owner/repo/compare/v1.1.0...v1.2.0
[1.1.0]: https://github.com/owner/repo/compare/v1.0.0...v1.1.0
[1.0.0]: https://github.com/owner/repo/releases/tag/v1.0.0
```

### Pre-release Versions

```markdown
## [2.0.0-beta.1] - 2024-01-10
## [2.0.0-alpha.3] - 2024-01-05
## [2.0.0-rc.1] - 2024-01-12
```

Order: alpha → beta → rc → stable

### Breaking Change Documentation

Breaking changes deserve extra attention:

```markdown
## [2.0.0] - 2024-02-01

### ⚠️ BREAKING CHANGES

- **API:** `getUserById()` now returns a Promise instead of callback
  - Migration: Replace `getUserById(id, callback)` with `await getUserById(id)`

- **Config:** Remove deprecated `legacyMode` option
  - Migration: Remove from config, use `compatMode` instead

### Added
- New async API for all user operations
```

### Good Version History

```markdown
## [Unreleased]

## [1.3.0] - 2024-01-20
### Added
- Add bulk export feature (#890)

## [1.2.1] - 2024-01-18
### Fixed
- Fix pagination on large datasets (#885)

## [1.2.0] - 2024-01-15
### Added
- Add filtering by date range (#870)
### Changed
- Improve search performance (#872)
```

### Bad Version History

```markdown
✗ Missing dates
## [1.2.0]

✗ Inconsistent format
## v1.2.0 - January 15, 2024
## [1.1.0] - 2024-01-10

✗ No comparison links
(Users can't see what changed between versions)

✗ Versions out of order
## [1.1.0]
## [1.3.0]
## [1.2.0]
```

### Checklist

- [ ] Version follows SemVer (MAJOR.MINOR.PATCH)
- [ ] Date in ISO 8601 format (YYYY-MM-DD)
- [ ] `[Unreleased]` section exists
- [ ] Comparison links at bottom
- [ ] Versions in descending order (newest first)
- [ ] Breaking changes clearly marked
