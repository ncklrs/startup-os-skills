---
title: Wiki Git Workflow
impact: MEDIUM-HIGH
tags: wiki, git, workflow, collaboration
---

## Wiki Git Workflow

**Impact: MEDIUM-HIGH**

GitHub wikis are Git repos. Treat them like code for better collaboration and history.

### Cloning the Wiki

```bash
# Wiki repo URL pattern
https://github.com/OWNER/REPO.wiki.git

# Clone
git clone https://github.com/owner/repo.wiki.git
cd repo.wiki

# List pages
ls *.md
```

### Basic Workflow

```bash
# Pull latest changes
git pull origin master

# Create/edit pages
vim New-Feature.md

# Update sidebar
vim _Sidebar.md

# Commit with descriptive message
git add -A
git commit -m "Add New-Feature documentation

- Document configuration options
- Add code examples
- Link from sidebar"

# Push to make changes live
git push origin master
```

### Commit Message Guidelines

```markdown
# Good commit messages
✓ "Add authentication documentation"
✓ "Update API reference for v2.0 breaking changes"
✓ "Fix broken links in Getting-Started"
✓ "Reorganize sidebar navigation"

# Bad commit messages
✗ "Update"
✗ "Fix docs"
✗ "WIP"
✗ "asdf"
```

### Working with Images

```bash
# Create images directory
mkdir -p images

# Add image
cp ~/screenshot.png images/feature-screenshot.png

# Reference in markdown
# Use relative path
![Feature Screenshot](images/feature-screenshot.png)

# Or absolute GitHub URL
![Feature](https://github.com/owner/repo/wiki/images/feature-screenshot.png)

# Commit
git add images/
git commit -m "Add screenshot for feature documentation"
```

### Branch Strategy (Optional)

For teams wanting review before publishing:

```bash
# Create branch for changes
git checkout -b docs/new-feature

# Make changes
vim New-Feature.md

# Commit
git commit -am "Document new feature"

# Push branch
git push origin docs/new-feature

# Create PR in wiki repo (requires GitHub CLI or web)
# After review, merge to master
git checkout master
git merge docs/new-feature
git push origin master
```

### Reverting Changes

```bash
# View history
git log --oneline

# Revert specific commit
git revert abc123
git push origin master

# Or reset to previous state (destructive)
git reset --hard abc123
git push --force origin master  # Careful!
```

### Multi-Author Workflow

```bash
# Always pull before editing
git pull origin master

# Make changes
vim Existing-Page.md

# Pull again before pushing (in case of concurrent edits)
git pull origin master

# Resolve conflicts if any
# Then push
git push origin master
```

### Useful Git Commands for Wiki

```bash
# See what changed
git diff

# See recent history
git log --oneline -10

# Find when a line was added
git blame Page-Name.md

# Search across all pages
git grep "search term"

# List all pages
ls *.md

# Check for broken internal links
grep -h "\[.*\](.*)" *.md | grep -v "http"
```

### Automation: Sync from Main Repo

Some teams keep docs in main repo and sync to wiki:

```bash
#!/bin/bash
# sync-wiki.sh

# Clone wiki
git clone https://github.com/owner/repo.wiki.git wiki-temp

# Copy docs
cp -r docs/* wiki-temp/

# Commit and push
cd wiki-temp
git add -A
git commit -m "Sync from main repo $(date +%Y-%m-%d)"
git push origin master

# Cleanup
cd ..
rm -rf wiki-temp
```

### Checklist

- [ ] Wiki repo cloned locally
- [ ] Pull before editing
- [ ] Descriptive commit messages
- [ ] Images in dedicated directory
- [ ] Push to publish changes
- [ ] Review history after major changes
