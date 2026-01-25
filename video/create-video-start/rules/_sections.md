# Create Video Start Rules

## Sections

### Pipeline Execution
Rules for orchestrating the skill pipeline.

- [pipeline-order.md](pipeline-order.md) — Execution order, dependencies, validation gates
- [error-handling.md](error-handling.md) — Retry logic, failure recovery, cleanup strategies

### Skill Invocation
Rules for invoking sub-skills via Claude CLI.

- [claude-cli-patterns.md](claude-cli-patterns.md) — `claude -p` patterns, tool permissions, HEREDOC usage
- [context-passing.md](context-passing.md) — Document flow, extraction patterns, format contracts

## Quick Reference

| Rule | When to Use |
|------|-------------|
| pipeline-order | Understanding step dependencies |
| error-handling | Handling failures gracefully |
| claude-cli-patterns | Constructing skill invocations |
| context-passing | Passing data between skills |
