# actions

## `conventional-pr-title`

Lints the pull request title against [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) and reports the result as PR comments and in the job summary. It needs `pull-requests: write` to comment, so it runs on `pull_request_target`. PR-controlled values never reach a shell, and it never checks out PR code.

Public repos must allow `pull_request_target` for this workflow under Settings → Actions → Policies.

### Example workflow

```yaml
name: PR
on:
  pull_request_target:
    branches: [main]
    types:
      - opened
      - edited
      - synchronize
      - reopened

permissions:
  pull-requests: write

jobs:
  validate:
    name: Validate PR title
    runs-on: ubuntu-latest
    steps:
      - uses: typeparameter/actions/conventional-pr-title@main
```
