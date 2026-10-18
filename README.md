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

jobs:
  release:
    uses: pkr-lab/.github/.github/workflows/release.yml@<commit-sha> # v1.0.0
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
    uses: pkr-lab/.github/.github/workflows/commitlint.yml@<commit-sha> # v1.0.0
```

Lokaler Hook: `git config core.hooksPath .githooks` mit einer Kopie von `hooks/commit-msg` unter `.githooks/`.

## Dokumentation

[Überblick und Eingaben](https://github.com/pkr-lab/pkr-lab-docs/blob/main/github-workflows/index.md) · [Releases](https://github.com/pkr-lab/pkr-lab-docs/blob/main/github-workflows/releases.md)

## Lizenz

MIT, siehe [LICENSE](LICENSE).
