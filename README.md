# actions

## `conventional-pr-title`

Lints the pull request title against [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) and writes the result to the job summary: either the lint error, or whether the PR would create a release. It needs only `pull-requests: read`, and is meant to run on `pull_request` (not `pull_request_target`).

### Example workflow

```yaml
name: PR
on:
  pull_request:
    branches: [main]
    types:
      - opened
      - edited
      - synchronize
      - reopened

permissions:
  pull-requests: read

jobs:
  validate:
    name: Validate PR title
    runs-on: ubuntu-latest
    steps:
      - uses: typeparameter/actions/conventional-pr-title@main
```
