# Security policy

PastureStack maintains legacy software. Historical tags and imported upstream releases may contain known or unknown vulnerabilities and are not automatically supported merely because they are available in this organization.

## Supported versions

Each repository must publish its own supported-version statement before making a maintained release. Unless a repository states otherwise:

- active migration branches receive best-effort security review;
- historical upstream tags are preserved but unsupported; and
- original upstream binaries and images remain end-of-life.

## Reporting a vulnerability

1. Use the affected repository's **Security** tab and **Report a vulnerability** option when available.
2. If private vulnerability reporting is unavailable, open a minimal public issue asking a maintainer to establish private contact. Do not include exploit details, secrets, customer information, or sensitive logs.
3. Include the affected repository and revision, impact, reproduction conditions, and a safe contact method in the private report.

Maintainers will acknowledge a complete private report as soon as practical, coordinate remediation, and credit reporters who wish to be credited. Response times are best effort; PastureStack does not provide a commercial security SLA.

## Scope

Reports about the PastureStack-maintained changes, build chain, releases, containers, and migration tooling are in scope. Vulnerabilities that affect unmodified upstream code may also need to be reported to the relevant upstream maintainer.
