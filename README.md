# Semantic Pull Requests

[![Launch in SuperPlane](https://superplane.com/badges/launch-in-superplane.svg)](https://app.superplane.com/install?repo=github.com/superplanehq/app_semantic_pull_requests)

Enforce **semantic pull request titles** on GitHub and track merged PRs by type — publish commit statuses, comment on invalid titles, and see merge trends in the console.

Built with [SuperPlane](https://superplane.com).

## How it works

1. **On pull request** — listen for `opened`, `edited`, `synchronize`, and `closed` events on a selected repository
2. **Validate title** — check the title against semantic types (`feat`, `fix`, `docs`, `chore`)
3. **Enforce** — on open, edit, or sync, publish a **Semantic PR title** commit status (success or failure) and comment on invalid titles when a PR is opened or edited
4. **Record merges** — when a PR is merged, increment the weekly count for its semantic `type` in the `semanticPrWeeklyStats` memory namespace
5. **Setup** — run with a `repository` parameter (`owner/repo`) to backfill weekly merge statistics for the current year
6. **Console** — totals by type this year and a bar chart of merged PRs by week

## Prerequisites

- [SuperPlane](https://superplane.com) account
- GitHub integration connected to the target repository

## Setup

Run **Setup** and enter the repository as `owner/repo` (for example, `superplanehq/superplane`).

## `GITHUB_TOKEN` secret

Add a secret named `GITHUB_TOKEN` on the **Fetch weekly stats** node. It is used only by **Setup** to backfill weekly merge statistics for the current year.

- **Private repositories:** required
- **Public repositories:** optional, but recommended to avoid unauthenticated API rate limits

### Fine-grained personal access token (recommended)

- **Repository access:** Only select repositories → choose the target repository
- **Repository permissions:**
  - **Metadata:** Read
  - **Pull requests:** Read
  - **Issues:** Read

## License

MIT
