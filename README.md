# Semantic Pull Requests

[![Launch in SuperPlane](http://superplane.com/badges/launch-in-superplane.svg)](https://app.superplane.com/install?repo=github.com/superplanehq/app_semantic_pull_requests)

Enforce **semantic pull request titles** on GitHub and track merged PRs by type — publish commit statuses, comment on invalid titles, and see merge trends in the console.

Built with [SuperPlane](https://superplane.com).

## How it works

1. **On pull request** — listen for `opened`, `edited`, `synchronize`, and `closed` events on a selected repository
2. **Validate title** — check the title against conventional commit types (`feat`, `fix`, `docs`, `chore`, `ci`, `build`, `test`, `refactor`, `perf`, `style`, `revert`)
3. **Enforce** — on open, edit, or sync, publish a **Semantic PR title** commit status (success or failure) and comment on invalid titles when a PR is opened or edited
4. **Record merges** — when a PR is merged, store `pr_number`, `title`, `type`, and `merged_at` in the `semanticPrMerges` memory namespace
5. **Setup** — backfill merged PRs from the current year via the GitHub API into memory
6. **Console** — merged PR count, bar chart by title, and a sortable table of all merges

## Prerequisites

- [SuperPlane](https://superplane.com) account
- GitHub integration connected to the target repository

## License

MIT
