# Contributing to PastureStack

Thank you for helping preserve and modernize the Rancher 1.6 ecosystem.

## Before starting

1. Search existing issues and pull requests.
2. Open or claim an issue for behavior changes, migrations, or large refactors.
3. Confirm which compatibility target and branch the change affects.
4. Never include credentials, private logs, customer data, or unreviewed binary artifacts.

## Change principles

- Preserve imported Git history and upstream tags. Do not rewrite published history.
- Keep modernization work separate from historical source preservation when practical.
- Prefer small, reviewable changes with a documented rollback path.
- Treat compatibility changes as product changes, even when they only update a dependency or build image.
- Retain copyright and license notices from upstream sources.
- Add third-party code only when its source and license are traceable and compatible with the target repository.

## Pull requests

A pull request should include:

- the problem and intended outcome;
- affected components and compatibility targets;
- testing or reproducibility evidence;
- security and migration impact;
- documentation or release-note impact; and
- any follow-up work intentionally left out of scope.

Use the repository's pull request template and keep the branch current with the target branch. Generated files and vendored dependencies must identify the command and source used to regenerate them.

## Testing legacy components

Many Rancher 1.6 components predate Go modules and current container tooling. Do not assume `go test ./...` or a modern base image is valid for every repository. Follow repository-specific build instructions and record the exact toolchain, container image, and commands used.

## Security reports

Do not disclose suspected vulnerabilities in a public issue. Follow [SECURITY.md](SECURITY.md).

## Conduct

Participation is governed by our [Code of Conduct](CODE_OF_CONDUCT.md).
