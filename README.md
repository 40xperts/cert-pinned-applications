# CERT Pinned Applications Threat Feed

## Purpose
This repository provides plain-text indicator lists that FortiGate can ingest as URL-based external threat feeds. Use it to distribute a curated set of certificate-pinned application endpoints so they can be monitored, restricted, or blocked by Fortinet appliances without manually editing each firewall.

## Repository Layout
- `application_list` – human-readable inventory of pinned applications and the endpoints they depend on.
- `url_list` – FortiGate-ready feed consumed by the firewall; each line is an indicator drawn from `application_list`.

## General Formatting Rules
- Files are ASCII text with Unix line endings (`\n`) and no BOM.
- Indicators use lowercase where possible to keep matching consistent.
- Blank lines are ignored but should be kept to a minimum.
- Lines starting with `#` are treated as comments for maintainers and are ignored by FortiGate.

## Updating `application_list`
This file tracks why a URL exists in the feed. Each entry should follow:

```
<application-name>|<platform>|<reason>|<url>
```

- `application-name`: Short display name (spaces allowed).
- `platform`: OS or ecosystem, e.g., `ios`, `android`, `windows`.
- `reason`: Brief justification such as `cert-pinned update service`.
- `url`: Exact URL or domain that appears in `url_list`.

Keep entries alphabetically sorted by application name to reduce merge conflicts. Duplicate URLs are allowed when multiple applications share them.

## Updating `url_list`
FortiGate expects a line-separated set of indicators. Use the exact value FortiGate must match (URL, FQDN, or subdomain). Examples:

```
# domains
api.example-app.com
cdn.example-app.com

# explicit URLs
https://downloads.example-app.com/updates/
```

- One indicator per line; do not add commas or quotes.
- Leave protocol off unless the path matters; FortiGate treats bare domains as FQDN matches and full URLs as literal strings.
- Avoid wildcard characters (`*`, `?`); FortiGate does not interpret them.
- Keep the list sorted and deduplicated before commit.

## Publishing the Feed to FortiGate
1. Commit and push changes to the repository.
2. In FortiGate, create a URL threat feed under **Security Fabric → External Connectors → Create New → URL**.
3. Point the feed URL to the raw Git hosting endpoint, for example: `https://raw.githubusercontent.com/<org>/<repo>/main/cert-pinned-applications/url_list`.
4. Enable the connector and reference it inside web filtering profiles, policies, or automation stitches as needed.

## Quality Checklist Before Commit
- Verify URLs resolve to the intended application endpoints.
- Ensure `application_list` and `url_list` stay in sync.
- Run a quick duplicate check (e.g., `sort -u`) and confirm the firewall still ingests the feed without errors.