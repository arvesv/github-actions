# Install hledger Action

GitHub Action to install the [`hledger`](https://hledger.org/) command-line accounting tool using [`eget`](https://github.com/zyedidia/eget).

Modeled after workflow usage in [`arvesv/Fellesregnskap`](https://github.com/arvesv/Fellesregnskap).

## Usage

### Basic

```yaml
steps:
  - uses: actions/checkout@v4

  - name: Install hledger
    uses: arvesv/github-actions/install-hledger@master

  - name: Verify installation
    run: hledger --version
```

### Specific Version

```yaml
steps:
  - uses: actions/checkout@v4

  - name: Install hledger 1.40
    uses: arvesv/github-actions/install-hledger@master
    with:
      version: '1.40'
```

### Custom Destination or Token

```yaml
steps:
  - uses: actions/checkout@v4

  - name: Install hledger
    uses: arvesv/github-actions/install-hledger@master
    with:
      token: ${{ secrets.GITHUB_TOKEN }}
      bin-dir: '/usr/local/bin'
```

## Inputs

| Input | Description | Default | Required |
|---|---|---|---|
| `version` | Version or tag of hledger to install (`latest` or release tag like `1.40`) | `latest` | No |
| `token` | GitHub token for GitHub Release API access (avoids rate limiting) | `${{ github.token }}` | No |
| `bin-dir` | Directory where the binary will be installed | `/usr/local/bin` | No |
| `cache` | Cache downloaded hledger binary across workflow runs | `'true'` | No |

## Outputs

| Output | Description |
|---|---|
| `version` | Installed hledger version output string |
| `bin-path` | Absolute path to the installed hledger executable |

---

*Authored with [Google Antigravity](https://antigravity.google).*
