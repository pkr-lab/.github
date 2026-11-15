# .github

Zentrale, wiederverwendbare GitHub-Workflows für alle Repos von pkr-lab: automatische Releases aus Conventional Commits und eine Prüfung der Commit-Nachrichten auf Pull Requests. Dazu ein lokaler `commit-msg`-Hook.

## Quickstart

Release-Workflow in einem Repo (`.github/workflows/release.yml`):

```yaml
name: Release

on:
  push:
    branches: [main]

permissions:
  contents: write
  issues: write
  pull-requests: write
  packages: write

concurrency:
  group: release-${{ github.ref }}
  cancel-in-progress: false

jobs:
  release:
    uses: pkr-lab/.github/.github/workflows/release.yml@<commit-sha> # <version>
```

Commit-Prüfung (`.github/workflows/commitlint.yml`):

```yaml
name: Commitlint

on:
  pull_request:
    branches: [main]

permissions:
  contents: read

jobs:
  commitlint:
    uses: pkr-lab/.github/.github/workflows/commitlint.yml@<commit-sha> # <version>
```

Lokaler Hook: `hooks/commit-msg` nach `.githooks/commit-msg` kopieren, ausführbar halten (`chmod +x .githooks/commit-msg`) und mit `git config core.hooksPath .githooks` einschalten.

## Dokumentation

[Überblick und Eingaben](https://github.com/pkr-lab/pkr-lab-docs/blob/main/github-workflows/index.md) · [Releases](https://github.com/pkr-lab/pkr-lab-docs/blob/main/github-workflows/releases.md)

## Lizenz

MIT, siehe [LICENSE](LICENSE).
