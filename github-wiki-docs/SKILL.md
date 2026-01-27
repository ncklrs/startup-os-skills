---
name: github-wiki-docs
description: Expert guidance for updating changelogs and GitHub wiki documentation. Use when writing CHANGELOG.md entries, updating release notes, creating or editing wiki pages, documenting features, maintaining API documentation, or syncing documentation with code changes. Use for "update the changelog", "document this feature", "add wiki page", "write release notes".
---

# GitHub Wiki & Changelog Documentation

Expert guidance for maintaining changelogs and GitHub wiki documentation — keeping docs accurate, discoverable, and in sync with code changes.

## Philosophy

Good documentation does three things:

1. **Answers questions before they're asked** — Users find what they need without searching
2. **Stays current** — Docs that lag behind code erode trust
3. **Tells a story** — Changelogs celebrate progress, wikis guide journeys

## How This Skill Works

When invoked, apply guidelines in `rules/` organized by:

- `changelog-*` — CHANGELOG.md entries, version formatting, release notes
- `wiki-*` — Wiki page structure, navigation, cross-linking
- `sync-*` — Keeping docs in sync with code changes

## Core Workflows

### Updating Changelog

1. **Identify changes** — Review commits, PRs, or diff since last release
2. **Categorize** — Added, Changed, Deprecated, Removed, Fixed, Security
3. **Write entries** — User-focused, not implementation details
4. **Link references** — PRs, issues, commits for traceability

### Updating Wiki

1. **Clone wiki repo** — `git clone https://github.com/owner/repo.wiki.git`
2. **Create/edit pages** — Markdown files become wiki pages
3. **Update navigation** — `_Sidebar.md` or `_Footer.md` if present
4. **Commit and push** — Changes appear immediately

## GitHub Wiki Essentials

### Wiki Repository

GitHub wikis are separate Git repos accessible at:
```
https://github.com/owner/repo.wiki.git
```

Clone, edit locally, push changes. More powerful than web editor.

### Special Files

| File | Purpose |
|------|---------|
| `Home.md` | Landing page (required) |
| `_Sidebar.md` | Navigation sidebar |
| `_Footer.md` | Footer on all pages |
| `_Header.md` | Header on all pages (rare) |

### Page Naming

- File name becomes URL: `Getting-Started.md` → `/wiki/Getting-Started`
- Use hyphens, not spaces or underscores
- Case-sensitive URLs

## Changelog Essentials

### Format (Keep a Changelog)

```markdown
# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [Unreleased]

## [1.2.0] - 2024-01-15
### Added
- New feature X (#123)

### Changed
- Improved performance of Y

### Fixed
- Bug in Z that caused crashes (#456)

[Unreleased]: https://github.com/owner/repo/compare/v1.2.0...HEAD
[1.2.0]: https://github.com/owner/repo/compare/v1.1.0...v1.2.0
```

### Categories

| Category | When to Use |
|----------|-------------|
| **Added** | New features |
| **Changed** | Changes to existing functionality |
| **Deprecated** | Soon-to-be removed features |
| **Removed** | Now removed features |
| **Fixed** | Bug fixes |
| **Security** | Vulnerability fixes |

## Anti-Patterns

- **Developer-speak** — "Refactored AbstractFactoryImpl" → "Faster startup time"
- **Missing links** — No PR/issue references for traceability
- **Stale docs** — Wiki pages that describe old behavior
- **Orphan pages** — Wiki pages with no links to them
- **Duplicate content** — Same info in README, wiki, and docs site
- **Wall of text** — No headings, code blocks, or structure
