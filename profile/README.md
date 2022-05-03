## CoinList

A collection of GitHub Actions that can be referenced in other GitHub repositories.

### Docker projects

#### docker_on_push.yml

[Workflow](./.github/workflows/docker_on_push.yml)

- Triggered on push to any branch
- Runs tests as `docker compose test`
- Uses `buildx` for multi-platrom Docker images support
- Docker layers are cached and stored as artifacts

#### docker_on_release.yml

[Workflow](./.github/workflows/docker_on_release.yml)

- Triggered on publishing a new release from GitHub UI
- Pushes built Docker image to AWS ECR
- Secrets: `AWS_ACCESS_KEY`, `AWS_SECRET_ACCESS_KEY`, `AWS_REGION`

### Usage

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
