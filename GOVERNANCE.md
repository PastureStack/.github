# Governance

PastureStack uses an open, repository-centered governance model.

## Roles

- **Contributors** propose changes through issues and pull requests.
- **Maintainers** triage work, review changes, and manage releases for repositories where they have write or maintain access.
- **Organization owners** manage organization policy, repository creation and transfer, security settings, and emergency access.

Permissions are granted according to the least privilege needed for current responsibilities. Repository administration does not automatically grant organization ownership.

## Decisions

- Routine decisions are made through reviewed pull requests.
- Compatibility changes, repository migrations, and release-policy changes require a linked issue with rationale and verification evidence.
- Material architecture changes should remain open for community review before implementation unless a security embargo applies.
- When consensus cannot be reached, the responsible maintainers document the decision and tradeoffs. Organization owners decide organization-wide policy disputes.

## Releases

Maintained releases must identify the source commit, toolchain, build procedure, artifacts, checksums, and compatibility scope. Historical upstream tags remain immutable. Rebuilt artifacts must not reuse an upstream tag in a way that obscures their different provenance.

## Security and emergencies

Maintainers may temporarily restrict access, disable automation, or revert a release to contain an active security incident. Emergency actions must be documented after sensitive details can safely be disclosed.

## Independence

PastureStack is not affiliated with or endorsed by Rancher Labs or SUSE. Project materials must distinguish PastureStack-maintained releases from upstream Rancher releases.
