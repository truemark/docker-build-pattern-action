# Docker Build Pattern Action

[![LICENSE](https://img.shields.io/badge/license-BSD3-green)](LICENSE)
[![Latest Release](https://img.shields.io/github/v/release/truemark/docker-build-pattern-action)](https://github.com/truemark/docker-build-pattern-action/releases)
![GitHub closed issues](https://img.shields.io/github/issues-closed/truemark/docker-build-pattern-action)
![GitHub closed pull requests](https://img.shields.io/github/issues-pr-closed/truemark/docker-build-pattern-action)

Builds and pushes a tagged image to a specified Docker repository. It relies on buildx to cache Docker layers wherever applicable.

## Examples
```yml
  read:
    runs-on: ubuntu-latest
    steps:
      - name: Build and push to Docker
        uses: truemark/docker-build-pattern-action@v2
        with:
          registry: "${{ secrets.DOCKER_HUB_REGISTRY }}"
          username: "${{ secrets.DOCKER_HUB_USERNAME }}"
          password: "${{ secrets.DOCKER_HUB_ACCESS_TOKEN }}"
          image: "test-tag:${{ github.run_number }}"
```

## Inputs
| Name     | Type   | Required | Description                                     |
|----------|--------|----------|-------------------------------------------------|
| registry | string | Yes      | Docker registry to log into.                    |
| username | string | Yes      | Docker username to log in with.                 |
| password | string | Yes      | Docker password to log in with.                 |
| image    | string | Yes      | Docker image tag to build and push.             |
| context  | string | No       | Location of the Dockerfile. Defaults to root.   |
