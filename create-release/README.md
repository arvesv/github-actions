# Create GitHub Release Action

GitHub Action to create a GitHub Release using the official GitHub CLI (`gh`). Supports automatic release notes generation, custom release notes/templates, asset file uploads, and draft/prerelease flags.

## Usage

### When triggered by a Git Tag push

```yaml
name: Release

on:
  push:
    tags:
      - 'v*'

permissions:
  contents: write

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Create Release
        uses: arvesv/github-actions/create-release@master
```

### Manual Trigger with Inputs

```yaml
name: Release

on:
  workflow_dispatch:
    inputs:
      version:
        description: 'Release version (e.g. v1.0.0)'
        required: true

permissions:
  contents: write

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Create Release
        uses: arvesv/github-actions/create-release@master
        with:
          tag: ${{ inputs.version }}
          title: 'Release ${{ inputs.version }}'
```

### Attaching Build Assets / Binaries

```yaml
steps:
  - uses: actions/checkout@v4

  # Build steps producing artifacts...

  - name: Create Release with Assets
    uses: arvesv/github-actions/create-release@master
    with:
      tag: ${{ github.ref_name }}
      files: |
        dist/*.tar.gz
        dist/*.zip
```

## Inputs

| Input | Description | Default | Required |
|---|---|---|---|
| `tag` | Tag name for the release (e.g. `v1.0.0`). Defaults to `github.ref_name` if triggered by a git tag. | `""` | No |
| `title` | Title of the release. Defaults to the tag name. | `""` | No |
| `body` | Release notes markdown text. | `""` | No |
| `body-path` | Path to a file containing release notes. | `""` | No |
| `generate-notes` | Automatically generate release notes using GitHub Release Notes API. | `'true'` | No |
| `draft` | Create release as a draft. | `'false'` | No |
| `prerelease` | Mark release as a prerelease. | `'false'` | No |
| `latest` | Mark release as latest (`true`, `false`, or `auto`). | `'auto'` | No |
| `target` | Target branch or commit SHA for the tag. | `""` | No |
| `files` | Space- or newline-separated asset file paths or globs to upload. | `""` | No |
| `allow-updates` | Update existing release and overwrite assets if the release already exists. | `'false'` | No |
| `token` | GitHub token with `contents: write` permission. | `${{ github.token }}` | No |

## Outputs

| Output | Description |
|---|---|
| `url` | URL of the created GitHub release. |
| `tag` | Tag name of the release. |

---

*Authored with [Google Antigravity](https://antigravity.google).*
