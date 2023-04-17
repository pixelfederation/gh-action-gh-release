# gh-action-gh-release

GitHub Action/Workflow for creating GitHub release.

## Usage as GitHub Action

Can be used also with self-hosted runners.

```yaml
name: 'Github release'

on:
  workflow_dispatch:
  push:
    tags:
      - '*'

jobs:
  gh-release:
    runs-on: ubuntu-latest
    steps:
      - name: release
        uses: pixelfederation/gh-action-gh-release@main
        with:
          # If enabled, respects commits between SemVer tag build num iterations instead of previous commited tag (eg: X.X.X-y_2 -> X.X.X-y_3)
          tag_num: false
          fetch_depth: '30'
          changelog_file: 'CHANGELOG.md'
```

## Usage as GitHub Workflow

Can not by used with self-hosted runners but logs are easier to read.

```yaml
name: 'Github release'

on:
  push:
    tags:
      - '*'

jobs:
  gh-release:
    uses: pixelfederation/gh-action-gh-release/.github/workflows/gh-release.yaml@main
    with:
      # If enabled, respects commits between SemVer tag build num iterations instead of previous commited tag (eg: X.X.X-y_2 -> X.X.X-y_3)
      tag_num: false
      fetch_depth: '30'
      changelog_file: 'CHANGELOG.md'
```
