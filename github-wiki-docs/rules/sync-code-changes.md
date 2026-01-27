---
title: Syncing Documentation with Code
impact: HIGH
tags: sync, automation, workflow, documentation-drift
---

## Syncing Documentation with Code

**Impact: HIGH**

Documentation drift — when docs don't match code — destroys user trust. Establish workflows to keep docs current.

### Documentation Update Triggers

| Code Change | Documentation to Update |
|-------------|------------------------|
| New feature | CHANGELOG, relevant wiki pages, API docs |
| API change | CHANGELOG (breaking!), API reference, examples |
| Config change | CHANGELOG, configuration wiki page |
| Bug fix | CHANGELOG (Fixed section) |
| Deprecation | CHANGELOG, deprecated feature page |
| Removal | CHANGELOG, remove from all docs |

### Workflow: PR with Code + Docs

Best practice: documentation ships with the code change.

```markdown
## PR Checklist
- [ ] Code changes complete
- [ ] Tests passing
- [ ] CHANGELOG.md updated
- [ ] Wiki pages updated (if applicable)
- [ ] README updated (if applicable)
```

### Wiki Repository Workflow

```bash
# Clone wiki (one-time)
git clone https://github.com/owner/repo.wiki.git

# Make changes
cd repo.wiki
vim Authentication.md

# Commit and push
git add -A
git commit -m "Update auth docs for OAuth 2.1 support"
git push origin master
```

### Keeping CHANGELOG in Sync

**Option 1: Update with each PR**
```bash
# In feature branch, before PR
echo "- Add dark mode toggle (#234)" >> CHANGELOG.md
git add CHANGELOG.md
git commit -m "Add changelog entry"
```

**Option 2: Update at release time**
```bash
# Review merged PRs since last release
gh pr list --state merged --base main --search "merged:>2024-01-01"

# Update CHANGELOG with all changes
# Then tag release
git tag -a v1.2.0 -m "Release 1.2.0"
git push origin v1.2.0
```

### Detecting Documentation Drift

Signs your docs are out of sync:
- User issues asking about documented features that changed
- Screenshots showing old UI
- Code examples that no longer compile
- API examples returning different responses

### Automation Opportunities

**GitHub Actions: Changelog validation**
```yaml
name: Changelog Check
on: pull_request

jobs:
  check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Check CHANGELOG updated
        run: |
          if ! git diff --name-only origin/main | grep -q "CHANGELOG.md"; then
            echo "Warning: CHANGELOG.md not updated"
            # Could be error for some projects
          fi
```

**PR Template**
```markdown
## Documentation

- [ ] CHANGELOG.md updated
- [ ] Wiki pages updated (if needed): _list pages_
- [ ] No documentation changes needed

### What documentation was updated?
_Describe changes or "N/A"_
```

### Good Sync Practices

```markdown
✓ Update docs in same PR as code change
  → Docs can't drift if they ship together

✓ Review docs in code review
  → "Did you update the wiki for this?"

✓ Link issues to doc changes
  → "Closes #123, updates wiki/Authentication"

✓ Schedule doc review
  → Monthly review of high-traffic pages
```

### Bad Sync Practices

```markdown
✗ "We'll update docs later"
  → Later never comes

✗ Separate doc team without code access
  → Can't stay current with changes

✗ No changelog discipline
  → Release notes become archaeology

✗ Copy-paste code examples
  → Examples diverge from actual code
```

### Checklist for Each Release

- [ ] CHANGELOG.md has entry for every user-facing change
- [ ] Version number follows SemVer
- [ ] Breaking changes documented with migration path
- [ ] Wiki pages referencing changed features updated
- [ ] README still accurate
- [ ] API docs regenerated (if auto-generated)
- [ ] Screenshots current (if UI changed)

### Checklist

- [ ] Documentation updates included in PR process
- [ ] CHANGELOG updated before merging
- [ ] Wiki cloned and accessible
- [ ] Regular doc review scheduled
- [ ] No known documentation drift
