# GitHub Actions

A collection of reusable GitHub Actions for workflows across repositories.

## Available Actions

| Action | Description | Path |
|---|---|---|
| [**install-hledger**](./install-hledger) | Installs the `hledger` command-line accounting tool via `eget`. | `arvesv/github-actions/install-hledger@master` |
| [**create-release**](./create-release) | Creates a GitHub Release with auto-generated notes and assets via GitHub CLI (`gh`). | `arvesv/github-actions/create-release@master` |

---

## Quick Start

### `install-hledger`

```yaml
- name: Install hledger
  uses: arvesv/github-actions/install-hledger@master
```

See [install-hledger/README.md](./install-hledger/README.md) for full documentation and options.

### `create-release`

```yaml
- name: Create Release
  uses: arvesv/github-actions/create-release@master
  with:
    tag: ${{ github.ref_name }}
```

See [create-release/README.md](./create-release/README.md) for full documentation and options.

---

*Authored with [Google Antigravity](https://antigravity.google).*
