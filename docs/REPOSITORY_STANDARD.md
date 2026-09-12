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
- publish SHA256 checksums for downloadable artifacts;
- document image names, tags, and digests;
- use only `vMAJOR.MINOR.PATCH` or `MAJOR.MINOR.PATCH` for every new
  PastureStack-owned Git tag, GitHub Release, package version, and image tag;
- reject brand, platform, candidate, rebuild, branch, or maintenance text in a
  new version (for example `-pasturestack.N`, `-windows-*`, or `-rcN`);
- express platform differences through distinct package or image names, and
  record source boundaries and rebuild metadata in OCI labels, SBOM,
  attestations, commits, and release notes instead of the version string;
- preserve every existing published tag as immutable history rather than
  deleting, moving, or reusing it;
- enforce the `Require numeric semantic version tags` GitHub tag ruleset on
  version-like tags (`v*` and digit-prefixed tags), without a bypass actor;
- avoid reusing upstream release tags for rebuilt artifacts; and
- publish compatibility and upgrade notes.

Package and container publication remains disabled until the repository has an approved release workflow and ownership policy.

### Package integrity and producer/consumer compatibility

Required when maintaining a release package or changing its installer contract:

- Use SHA256 for both the outer archive and the payload integrity checks consumed
  by the installer. A valid outer digest does not prove the contents satisfy the
  installer contract, and checksums do not replace trusted release provenance.
- Packages consumed by the shared host installer must contain a single package
  root with `SHA256SUMS` and `SHA256SUMSSUM`. Verify the payload and manifest with
  the consumer's exact path and working-directory semantics, using safe extraction
  confined to the isolated package root. SHA256 values are 64 hexadecimal digits.
- Current installers must reject missing, malformed or mismatching SHA256 data;
  never fall back to SHA1 or MD5. Legacy SHA1 manifests may be additional metadata
  only for documented older consumers; they do not satisfy current acceptance.
  This does not require rewriting Git object identifiers or immutable history.
- Trace the actual producer release through Server's final image, inherited
  archives, advertised download endpoint and consumer verifier. Updating source
  packaging alone does not update a pinned or inherited release asset. Keep the
  affected README, compatibility notes and release coordinates aligned.
- Test the final candidate archive with the actual consumer verifier: accept the
  valid package; reject missing manifests, SHA1-only metadata, invalid manifests
  and modified payloads. Source markers, filename checks, reconstructed fixtures
  and outer checksums alone are not sufficient evidence.
- Changes to this chain, or a confirmed gap in it, require download, installation
  and registration in an isolated fresh-host environment without an existing
  package cache. Existing-host workloads, `/ping` and unrelated feature tests do
  not prove registration. Check direct sibling packages sharing that verifier;
  do not rerun registration for unrelated text or layout changes.
- Publish corrected bytes under a new numeric version; never replace a published
  asset or ask operators to manufacture missing checksum files. Record a known
  incompatibility as unresolved even when other feature tests passed.

The machine-readable policy records these requirements, but does not itself
install or enforce a CI check. Automatic enforcement must be verified in each
affected release workflow before being claimed.

## 8. Migration acceptance

A repository is accepted only when the [migration checklist](MIGRATION_CHECKLIST.md) is complete and evidence is linked from a migration issue. Exceptions must identify the owner, risk, and follow-up deadline.
