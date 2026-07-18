# PastureStack organization defaults

This public `.github` repository defines the default community health files and optional workflow templates for repositories in the [PastureStack](https://github.com/PastureStack) organization.

PastureStack is an independent community effort to preserve, audit, and modernize the Rancher 1.6 ecosystem. It is not affiliated with or endorsed by Rancher Labs or SUSE.

## What this repository provides

- Default contribution, governance, support, security, issue, and pull request guidance.
- A documented [repository standard](docs/REPOSITORY_STANDARD.md).
- A repeatable [migration checklist](docs/MIGRATION_CHECKLIST.md).
- A machine-readable [repository policy](standards/repository.yml) for future automation.
- Optional workflow templates for migration integrity and Go module projects.

GitHub applies supported community health files from this repository only when a target repository does not provide its own file of the same type. Repository-specific guidance always takes precedence.

## Important limitations

- Licenses are never inherited. Every migrated repository must contain its own `LICENSE` file.
- Files inherited from this repository are not copied into target repositories or their clones.
- Workflow templates are optional starters. They are not installed automatically.
- Repository settings and branch rules must still be applied and verified per repository on GitHub Free.

## Repository layout

```text
.github/
  ISSUE_TEMPLATE/            Default organization issue forms
  PULL_REQUEST_TEMPLATE.md   Default pull request checklist
docs/                        Human-readable migration standards
profile/README.md            PastureStack organization profile
standards/repository.yml     Machine-readable policy baseline
workflow-templates/          Optional GitHub Actions starters
```

Changes to this repository affect the contributor experience across the organization and should receive the same review as production policy changes.
