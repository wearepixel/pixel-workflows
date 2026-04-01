# pixel-workflows

Canonical workflow and config files synced to all Pixel client repos via [BetaHuhn/repo-file-sync-action](https://github.com/BetaHuhn/repo-file-sync-action).

## How it works

On every push to `master` (and daily at 1am UTC), the sync workflow pushes files from `files/` to all configured client repos. It only commits if a file has changed.

## Synced files

| File | Purpose |
|------|---------|
| `.github/dependabot.yml` | Weekly dependency updates for composer, npm, and GitHub Actions |
| `.github/workflows/dependabot-auto-merge.yml` | Auto-merges minor/patch Dependabot PRs after tests pass |
| `.editorconfig` | Consistent editor settings (LF line endings, 4-space indent) |
| `.gitattributes` | Correct diffs and line endings per file type |
| `pint.json` | Laravel Pint code style rules |

## Adding a new client repo

1. If the repo is in a new org, install the **Pixel Workflows** GitHub App on that org
2. Create a `.sync-{org}.yml` config file (copy an existing one)
3. Add a new job to `.github/workflows/sync.yml` for that org
4. Add the repo to the appropriate `.sync-{org}.yml`

If the repo is in an existing org (e.g. `wearepixel`), just add it to `.sync-wearepixel.yml`.

## Configured repos

| Org | Repos |
|-----|-------|
| `wearepixel` | rethread, paper, astrid |
| `nourishd` | nourishd |
| `pulsewise` | pulsewise |
