# GitHub Actions

A collection of GitHubActions that can be referenced in other GitHub repositories.

## Actions

### Docker

- [docker_on_push](./.github/workflows/docker_on_push.yml) - Install Docker project and run tests
- [docker_on_release](./.github/workflows/docker_on_release.yml) - Bump version and deploy Docker project on release

## Usage

Create this files in `<repo_root>/.github/workflows` directory.

```yaml
# on_push.yml
name: Test

on:
  push: {}
  workflow_dispatch: {}

jobs:
  tests:
    uses: coinlist/.github/.github/workflows/ruby_on_push.yml@main
    with:
      image: ${{ github.event.repository.name }}
      tag: ${{ github.sha }}
```

```yaml
# on_release.yml
name: Release

on:
  release: {}

jobs:
  release:
    uses: coinlist/.github/.github/workflows/ruby_on_release.yml@main
    with:
      image: ${{ github.event.repository.name }}
      tag: latest
```