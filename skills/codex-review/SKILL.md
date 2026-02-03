---
name: codex-review
description: Hand off code review to OpenAI Codex CLI. Use when asked to "review code with codex",
             "codex review", "get a second opinion on code", "review my changes", "review this PR",
             or when you want AI-powered code review from a different model perspective.
argument-hint: [uncommitted|PR #|branch|commit SHA]
---

# Codex Code Review

Hand off code review tasks to OpenAI's Codex CLI for an independent AI perspective on code changes.

## How This Skill Works

When invoked, this skill launches the Codex CLI's `review` command in the terminal to analyze code changes. Codex provides a fresh perspective using OpenAI's models, which can catch different issues than Claude might.

## When to Use This Skill

- Getting a **second opinion** on code changes before committing
- Reviewing **uncommitted work** (staged, unstaged, or untracked files)
- Reviewing a **pull request** against a base branch
- Analyzing a **specific commit** for potential issues
- Cross-validating Claude's own code suggestions

## Review Modes

### 1. Uncommitted Changes (Default)
Review all local changes not yet committed:

```bash
codex review --uncommitted
```

### 2. PR Review (Against Base Branch)
Review changes between current branch and a base branch:

```bash
codex review --base main
```

### 3. Specific Commit
Review changes introduced by a single commit:

```bash
codex review --commit <SHA>
```

### 4. Custom Instructions
Add specific review focus areas:

```bash
codex review --uncommitted "Focus on security vulnerabilities and error handling"
```

## Execution Instructions

**IMPORTANT**: When this skill is invoked, Claude MUST execute the appropriate `codex review` command using the Bash tool. Do not just describe what to do — actually run the command.

### Argument Handling

| User Says | Command to Run |
|-----------|----------------|
| `/codex-review` (no args) | `codex review --uncommitted` |
| `/codex-review uncommitted` | `codex review --uncommitted` |
| `/codex-review PR` or `/codex-review main` | `codex review --base main` |
| `/codex-review PR #123` | First `gh pr checkout 123`, then `codex review --base main` |
| `/codex-review <branch>` | `codex review --base <branch>` |
| `/codex-review <sha>` | `codex review --commit <sha>` |

### Execution Steps

1. **Determine review mode** from arguments (default: uncommitted)
2. **Run the codex review command** using Bash tool
3. **Present the results** to the user with any notable findings highlighted
4. **Offer follow-up actions** (apply suggestions, create issues, etc.)

## Command Reference

```bash
# Full options
codex review [OPTIONS] [PROMPT]

Options:
  --uncommitted          Review staged, unstaged, and untracked changes
  --base <BRANCH>        Review changes against the given base branch
  --commit <SHA>         Review the changes introduced by a commit
  --title <TITLE>        Optional commit title to display in review summary
  -c, --config <k=v>     Override config (e.g., -c model="o3")
  -h, --help             Print help
```

## Example Workflows

### Quick Local Review
```bash
# Review everything you've changed locally
codex review --uncommitted
```

### Pre-PR Review
```bash
# Review your feature branch against main before opening PR
codex review --base main "Check for breaking changes and missing tests"
```

### Focused Security Review
```bash
# Security-focused review of uncommitted changes
codex review --uncommitted "Focus on: SQL injection, XSS, auth bypass, secrets exposure"
```

## Integration Notes

- Codex CLI must be installed and authenticated (`codex login`)
- Reviews run non-interactively and output results to terminal
- Use `codex apply` after review to apply any suggested diffs
- Combine with Claude's own review for comprehensive coverage
