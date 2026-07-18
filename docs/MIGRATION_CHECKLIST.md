# Repository migration checklist

Copy this checklist into the repository's migration issue and link supporting evidence.

## Source and ownership

- [ ] Record upstream URL, owner, default branch, source commit, and retrieval date.
- [ ] Confirm the target repository name and visibility.
- [ ] Confirm license compatibility and preserve required notices.
- [ ] Add the PastureStack independence and maintenance-status notice.

## Git data

- [ ] Compare commit count and representative commit IDs.
- [ ] Compare all required branches and tags.
- [ ] Preserve published tags without moving or rewriting them.
- [ ] Inventory Git LFS objects and verify they are available locally and remotely.
- [ ] Inventory submodules and replace inaccessible URLs only with documented equivalents.
- [ ] Inventory releases, release notes, and downloadable assets.

## Sensitive and unsuitable content

- [ ] Scan current files and history for credentials and private data.
- [ ] Review large binaries, archives, generated files, and vendored dependencies.
- [ ] Record any removed content and the legal or security reason for removal.
- [ ] Obtain owner approval before making a staged private import public.

## Build and operation

- [ ] Document the historical build toolchain.
- [ ] Reproduce the build or record a bounded, actionable blocker.
- [ ] Record required base images and external dependencies.
- [ ] Document runtime, database, API, and upgrade compatibility.
- [ ] Verify that existing automation cannot publish or deploy unexpectedly.

## GitHub configuration

- [ ] Confirm the PastureStack security configuration is assigned.
- [ ] Confirm `GITHUB_TOKEN` defaults to read-only.
- [ ] Review all imported workflows before enabling them.
- [ ] Configure public default-branch protection after the first reliable checks exist.
- [ ] Configure topics, description, homepage, and archived status.
- [ ] Enable private vulnerability reporting for maintained public repositories.

## Release readiness

- [ ] Define maintained branches and supported versions.
- [ ] Define tag and artifact naming that cannot be confused with upstream releases.
- [ ] Document release ownership, checksums, image digests, and rollback.
- [ ] Close the migration issue with links to verification evidence and deferred risks.
