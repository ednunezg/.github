# GitHub Actions

A collection of GitHubActions that can be referenced in other GitHub repositories.

## Actions

### Ruby

- [ruby_on_push](./.github/workflows/ruby_on_push.yml) - Install Ruby project and run tests
- [ruby_on_release](./.github/workflows/ruby_on_release.yml) - Bump version and deploy Ruby project on release

## Usage

Create this files in `<repo_root>/.github/workflows` directory.

```yaml
# on_push.yml
name: Test

on:
  push: {}

jobs:
  tests:
    uses: coinlist/github_actions/.github/workflows/ruby_on_push.yml@main
    with:
      image: ${{ github.repository }}
```

```yaml
# on_release.yml
name: Release

on:
  release: {}

jobs:
  release:
    uses: coinlist/github_actions/.github/workflows/ruby_on_release.yml@main
    with:
      image: ${{ github.repository }}
```