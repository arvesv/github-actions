# GitHub Actions

A collection of reusable GitHub Actions for workflows across repositories.

## Available Actions

| Action | Description | Path |
|---|---|---|
| [**install-hledger**](./install-hledger) | Installs the `hledger` command-line accounting tool via `eget`. | `arvesv/github-actions/install-hledger@master` |

---

## Quick Start

### `install-hledger`

```yaml
- name: Install hledger
  uses: arvesv/github-actions/install-hledger@master
```

See [install-hledger/README.md](./install-hledger/README.md) for full documentation and options.

---

*Authored with [Google Antigravity](https://antigravity.google).*
