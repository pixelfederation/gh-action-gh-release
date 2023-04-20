# gh-action-gh-release

GitHub Workflow for creating GitHub release.

## Usage

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
