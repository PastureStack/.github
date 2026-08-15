# GitHub automation baseline

PastureStack uses GitHub's no-cost features for public repositories to reduce repetitive maintenance while keeping releases and deployments explicit.

## Organization baseline

- GitHub Actions is enabled for every repository.
- Repository workflows may use GitHub-owned actions and reusable workflows from `PastureStack/.github`.
- Workflow tokens are read-only by default. A job must declare any additional permission it needs.
- Artifacts and workflow logs are retained for 30 days.
- Workflows from first-time and external contributors require approval.
- Dependency graph, automatic dependency submission, Dependabot alerts, grouped security updates, secret scanning, push protection, malware alerts, and private vulnerability reporting are enabled where GitHub supports them.
- `PastureStack-org-config-1` enforces the default security baseline, including CodeQL default setup, on repositories with a supported language.
- `PastureStack-compatible-security` enforces the same no-cost baseline without replacing reviewed advanced CodeQL workflows or enabling CodeQL for repositories without a supported language.
- Every default branch is protected against force pushes and deletion, requires linear history, and enforces resolved review conversations.
- Pull requests may update an out-of-date branch, merge automatically after their configured requirements pass, and delete their source branch after merging.

Required pull requests and status checks are added per repository only after its stable check names and compatibility path are verified. This keeps the migration baseline usable without weakening default-branch integrity.

## Continuous integration

Repositories without a component-specific workflow call the reusable repository-integrity workflow in this repository. The shared workflow verifies Git objects, required clone-visible files, and GitHub's practical file-size limit. Component-specific build and test workflows remain in their own repositories because toolchains and compatibility requirements differ.

Centralizing the baseline means a maintenance fix is made once instead of being copied into every repository.

## Delivery and releases

CI does not deploy to a production control plane. Release workflows may publish versioned GitHub Releases or GHCR images only after repository-specific build, test, license, provenance, rollback, and compatibility checks are defined.

Published image tags and release versions use normal incrementing semantic versions. Digests and attestations remain machine-verifiable metadata and are not embedded in user-facing version strings.

The organization repository provides an opt-in container-release workflow. It validates a numeric semantic version, publishes only that version tag to GHCR, and records GitHub build provenance. Repositories must still add their own tests, license checks, SBOM generation, vulnerability gate, and rollback acceptance before adopting the release workflow.

## Cost guardrails

PastureStack uses standard GitHub-hosted runners for public repositories. Larger runners, GitHub Code Quality billing, paid private-repository security features, and automatic production deployment are outside this baseline.
