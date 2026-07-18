# PastureStack repository standard

This standard applies to repositories imported into or created under PastureStack. **Required** items are migration acceptance criteria. **Recommended** items may be deferred only with a documented reason.

## 1. Identity and provenance

Required:

- Use a lowercase, kebab-case repository name and avoid adding a version to the name unless needed to resolve a genuine collision.
- Record the upstream repository URL, immutable source commit, source default branch, imported branches, and imported tags.
- Preserve upstream Git history and published tags. Never move or replace an upstream tag.
- Distinguish PastureStack-maintained releases from upstream releases in names, tags, images, and documentation.
- State that PastureStack is an independent project and is not affiliated with Rancher Labs or SUSE.

## 2. Visibility and access

Required:

- Prefer public visibility after license, provenance, and secret review.
- Use private staging only when unresolved sensitive content or provenance requires it.
- Grant access through teams or explicit repository roles; do not increase organization-wide base permission.
- Keep visibility changes, deletion, and repository transfer restricted to organization owners.

## 3. Default branch and history

Required:

- Preserve the source default branch during import and verification.
- Rename to `main` only after references, automation, badges, submodules, release scripts, and documentation are updated.
- Enable branch protection or a repository ruleset before accepting general contributions to a public repository.

Recommended public default-branch rules:

- require pull requests;
- require at least one approval;
- dismiss stale approvals after new commits;
- require conversation resolution;
- block force pushes and deletion;
- apply rules to administrators, with a documented emergency process; and
- add required status checks only after their names and reliability are stable.

GitHub Free requires these rules to be managed per public repository.

## 4. Required repository content

Required in every repository:

- `README.md` with purpose, status, upstream source, build instructions, compatibility, and independence notice;
- `LICENSE` containing the repository's actual license;
- upstream copyright and notice files required by that license;
- reproducible build or restoration instructions; and
- a repository-specific support statement when it differs from the organization default.

The organization `.github` repository supplies default community files, but it cannot supply a repository's license or clone-visible documentation.

## 5. Security and automation

Required:

- Keep the default `GITHUB_TOKEN` read-only; grant narrower write permissions inside an individual job only when required.
- Require approval before workflows from external contributors run.
- Never place credentials in workflow files, build logs, examples, images, history, or release assets.
- Use immutable action commit SHAs for new workflows. Record the corresponding release tag in a comment.
- Enable the PastureStack security configuration and grouped Dependabot security updates.

Recommended:

- Use OpenID Connect instead of long-lived cloud credentials.
- Add artifact attestations and checksums for maintained public releases.
- Keep Actions artifacts and logs only as long as operationally required.

## 6. Build and compatibility

Required:

- Document the exact supported toolchain and container runtime.
- Do not silently replace legacy dependencies or base images solely to make a build pass.
- Record intentional behavior changes and provide rollback or migration guidance.
- Verify vendored and generated content against its source and regeneration procedure.

Recommended:

- Separate preservation branches from modernization branches when changes cannot remain backward-compatible.
- Prefer reproducible containers or scripts over undocumented developer-machine state.

## 7. Releases and packages

Required for maintained releases:

- identify the source commit and build inputs;
- publish checksums for downloadable artifacts;
- document image names, tags, and digests;
- avoid reusing upstream release tags for rebuilt artifacts; and
- publish compatibility and upgrade notes.

Package and container publication remains disabled until the repository has an approved release workflow and ownership policy.

## 8. Migration acceptance

A repository is accepted only when the [migration checklist](MIGRATION_CHECKLIST.md) is complete and evidence is linked from a migration issue. Exceptions must identify the owner, risk, and follow-up deadline.
