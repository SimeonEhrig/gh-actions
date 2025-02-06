# QED Github Actions

Github Actions for packages of the QuantumElectrodynamics.jl ecosystem.

# Action build-docs: Build and Deploy QED documentation

The action finds all QED dependencies for building the documentation, sets the dependencies to the current version of the dev branch and build and deploys the documentation.

## Usage

```yaml
name: Build and deploy documentation

on:
  push:
    branches:
      - main
      - dev
    tags: '*'
  pull_request:

jobs:
  build:
    permissions:
      contents: write
      statuses: write
    runs-on: ubuntu-latest
    steps:
      - uses: QEDjl-project/gh-actions/build-docs@v1
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

## Input Parameter

- `github-token`: Pass `secrets.GITHUB_TOKEN` to the action so that it can push the built documentation to the `gh-pages` branch.
- `julia-version` (optional, default='1.10'): Julia version built to create the documentation.
- `github-tools-url` (optional, default='https://github.com/QEDjl-project/QuantumElectrodynamics.jl.git'): URL of the Git repository from which the tool for setting up the build environment is downloaded.
- `github-tools-branch` (optional, default='dev'): Branch of the Git repository from which the tool for setting up the build environment is downloaded.
