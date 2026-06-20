# Agent Guidelines — Semantic Pull Requests

This file provides context for AI agents operating on this canvas.

## What this app does

Semantic Pull Requests enforces semantic PR title conventions on GitHub repositories. It validates titles against types like `feat`, `fix`, `docs`, `chore`, publishes commit statuses, comments on invalid titles, and tracks merged PRs by type in a weekly bar chart.

## Flows

### PR validation flow
```
On Pull Request (opened/edited/synchronize) → Validate Title (JS runner)
  → (valid) Publish Success Status
  → (invalid) Publish Failure Status → Comment on PR
```

### Merge tracking flow
```
On Pull Request (closed + merged) → Filter (merged only) → Parse Type → Upsert Weekly Stats
```

### Setup flow (manual)
```
Run Setup → Fetch Weekly Stats (JS runner) → Backfill Memory
```

## Memory

- `semanticPrWeeklyStats` — weekly merge counts by type (feat, fix, docs, chore, etc.)

## What's safe to change

- **Accepted title types** — the JS runner script that validates titles. Add or remove types.
- **Comment text** — the `github.createIssueComment` node's body
- **Commit status context** — the `context` field on status nodes (default: "Semantic PR title")

## What not to change

- **Memory namespace** (`semanticPrWeeklyStats`) — the console reads from this
- **The merge tracking flow** — it feeds the console bar chart

## Common issues

**Setup fails on private repos:**
Add a `GITHUB_TOKEN` secret to the **Fetch weekly stats** runner node. Needs Pull requests:Read permission.

**Titles not being checked:**
The On Pull Request trigger must be connected to your GitHub integration and configured with your repository name.

**Console shows no data:**
Run the **Setup** trigger first to backfill weekly stats for the current year.
