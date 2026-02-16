[![oz and dotenvx](https://dotenvx.com/assets/img/oz/oz-plus-dotenvx.png)](https://warp.dev/oz)

> Wizard of Drift - Checks `.env*` key drift on pull requests with Warp Agent and posts a PR review comment.

## Inputs

- `warp_api_key` (required)
- `warp_agent_profile` (optional)
- `github_token` (required)

## Usage

```yaml
name: Env Drift Review

on:
  pull_request:
    types: [opened, synchronize, reopened]

permissions:
  contents: read
  pull-requests: write

jobs:
  env-drift:
    runs-on: ubuntu-latest
    steps:
      - uses: dotenvx/wizard-of-drift@v1
        with:
          warp_api_key: ${{ secrets.WARP_API_KEY }}
          github_token: ${{ secrets.GITHUB_TOKEN }}
          warp_agent_profile: "" # optional
```

## Notes

- Runs on `pull_request` only.
- Compares key names only (not values).
- Excludes `.env.keys` (which should never be committed to code)
