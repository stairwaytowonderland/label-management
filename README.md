# Label Management

[![Continuous integration](https://github.com/stairwaytowonderland/label-management/actions/workflows/ci.yaml/badge.svg)](https://github.com/stairwaytowonderland/label-management/actions/workflows/ci.yaml)
[![GitHub latest release](https://img.shields.io/github/v/release/stairwaytowonderland/label-management?include_prereleases&logo=rocket)](https://github.com/stairwaytowonderland/stairwaytowonderland/label-management/releases)
[![GitHub last commit](https://img.shields.io/github/last-commit/stairwaytowonderland/label-management?logo=git)](https://github.com/stairwaytowonderland/stairwaytowonderland/label-management/commits/main)
[![GitHub license](https://img.shields.io/github/license/stairwaytowonderland/label-management?logo=opensourceinitiative&labelCol&color=yellow&logoColor=white)](https://github.com/stairwaytowonderland/stairwaytowonderland/label-management/tree/main/LICENSE)
[![semantic-release: conventionalcommits](https://img.shields.io/badge/semantic--release-cc-FE5196?logo=semantic-release)](https://github.com/semantic-release/semantic-release)
[![pre-commit](https://img.shields.io/badge/pre--commit-FAB040?logo=pre-commit&logoColor=black)](https://github.com/pre-commit/pre-commit)

A centralized label management repository. :label:

## :cactus: Project structure

> [!NOTE]
>
> `tree -a -F -L 3 -I '.git|.vscode' --gitignore --dirsfirst .`

```none
./
├── .github/
│   ├── workflows/
│   │   ├── ci.yaml
│   │   ├── conventional-commit.yaml
│   │   ├── create-labels.yaml
│   │   ├── import-csv-issues.yaml
│   │   ├── pre-commit.yaml
│   │   ├── publish.yaml
│   │   ├── release.yaml
│   │   ├── repository-created.yaml
│   │   └── sync-labels.yaml
│   └── dependabot.yml
├── .editorconfig
├── .gitignore
├── .markdownlint.json
├── .pre-commit-config.yaml
├── .prettierignore
├── .prettierrc
├── .releaserc
├── CHANGELOG.md
├── LICENSE
├── README.md
├── TODO.csv
└── TODO.example.csv
```

---

## :arrows_counterclockwise: Reusable Workflows

### `create-labels`

**Description:**
Reusable workflow to validate commit messages in pull requests or caller-defined refs.

**Usage Example:**

```yaml
uses: stairwaytowonderland/label-management/.github/workflows/create-labels.yaml@main
with:
  dry-run: true
  update-labels: true
secrets: inherit
```

**Inputs:**

| Name              | Description                                                               | Required | Type    | Default |
| ----------------- | ------------------------------------------------------------------------- | -------- | ------- | ------- |
| `dry-run`         | Ref of this shared actions repository to checkout                         | No       | boolean | `false` |
| `update-existing` | Whether to update existing labels (e.g. rename, change color/description) | No       | boolean | `false` |
| `ref`             | Ref of this shared actions repository to checkout                         | No       | string  | `v1`    |

**Secrets:**

| Name           | Description                                                                     |
| -------------- | ------------------------------------------------------------------------------- |
| `github-token` | Optional token with permissions to create issues (falls back to `GITHUB_TOKEN`) |

### `sync-labels`

**Description:**
Sync a defined set of labels across all repositories in the organization. This workflow can be called by other workflows
(e.g. on a schedule or via manual trigger) to ensure consistent labeling across repos.

**Usage Example:**

```yaml
uses: stairwaytowonderland/label-management/.github/workflows/sync-labels.yaml@main
with:
  dry-run: true
  update-labels: true
secrets: inherit
```

**Inputs:**

| Name              | Description                                                               | Required | Type    | Default |
| ----------------- | ------------------------------------------------------------------------- | -------- | ------- | ------- |
| `dry-run`         | Ref of this shared actions repository to checkout                         | No       | boolean | `false` |
| `update-existing` | Whether to update existing labels (e.g. rename, change color/description) | No       | boolean | `false` |
| `ref`             | Ref of this shared actions repository to checkout                         | No       | string  | `v1`    |

**Secrets:**

| Name           | Description                                                                     |
| -------------- | ------------------------------------------------------------------------------- |
| `github-token` | Optional token with permissions to create issues (falls back to `GITHUB_TOKEN`) |

---

## :sparkles: Contributing

### :robot: Commit Message Guidelines

- Write clear, concise commit messages that follow the
  [![conventional-commit](https://img.shields.io/badge/conventional--commit-FE5196?logo=conventionalcommits&logoColor=white)](https://www.conventionalcommits.org/)&nbsp;standard.
- The allowed _prefixes_ for this project are the following:

    ```json
    [
      "build",
      "chore",
      "ci",
      "docs",
      "feat",
      "fix",
      "perf",
      "refactor",
      "revert",
      "style",
      "test"
    ]
    ```

> [!NOTE]
>
> See [Contributing Guidelines](https://github.com/stairwaytowonderland/label-management?tab=contributing-ov-file#contributing-guidelines)
> for more information.
