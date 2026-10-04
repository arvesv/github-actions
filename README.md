# GitHub Actions

A collection of reusable GitHub Actions for workflows across repositories.

## Available Actions

| Action | Description | Path |
|---|---|---|
| [**install-hledger**](./install-hledger) | Installs the `hledger` command-line accounting tool via `eget` with binary caching. | `arvesv/github-actions/install-hledger@v1` |
| [**create-release**](./create-release) | Creates or updates a GitHub Release with auto-generated notes and assets via `gh`. | `arvesv/github-actions/create-release@v1` |

---

## Quick Start

Actions can be referenced using the major release tag (e.g. `@v1`) or the branch (`@master`).

### `install-hledger`

```yaml
- name: Install hledger
  uses: arvesv/github-actions/install-hledger@v1
```

See [install-hledger/README.md](./install-hledger/README.md) for full documentation and options.

### `create-release`

```yaml
- name: Create Release
  uses: arvesv/github-actions/create-release@v1
  with:
    tag: ${{ github.ref_name }}
```

See [create-release/README.md](./create-release/README.md) for full documentation and options.

---

*Authored with [Google Antigravity](https://antigravity.google).*
