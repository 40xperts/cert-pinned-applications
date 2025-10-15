# FortiGate External Threat Feeds

## Purpose
This directory contains plain-text indicator lists that FortiGate can ingest as external threat feeds. Use them to distribute curated certificate-pinned application data so Fortinet appliances can monitor, restrict, or block traffic without editing each firewall manually.

## Repository Layout
- `application_list` – human-readable inventory describing which applications depend on which indicators.
- `domain_list` – FortiGate-ready FQDN feed; each entry is a domain or subdomain derived from the inventory.
- `url_list` – FortiGate-ready URL feed; each entry is a full URL that requires path-level matching.

## General Formatting Rules
- Files are ASCII text with Unix line endings (`\n`) and no BOM.
- Prefer lowercase indicators to keep matches consistent.
- Blank lines are ignored but should be minimized to simplify diff review.
- Lines starting with `#` are comments for maintainers and are ignored by FortiGate.
- Sort and deduplicate before committing to avoid connector churn.

## Maintaining `application_list`
`application_list` documents the reason each indicator exists. Record entries using pipe-delimited fields:

```
<application-name>|<platform>|<reason>|<indicator>
```

- `application-name`: Concise display name (spaces allowed).
- `platform`: OS or ecosystem, e.g., `ios`, `android`, `windows`.
- `reason`: Short justification such as `cert-pinned telemetry` or `mandatory update channel`.
- `indicator`: The exact domain or URL string present in `domain_list` or `url_list`.

Keep the file alphabetized by `application-name`. Duplicate indicators are acceptable when multiple applications share the same endpoint.

## Maintaining `domain_list`
Use `domain_list` for bare domains or subdomains that FortiGate should evaluate using FQDN matching.

```
# example domains
api.example-app.com
cdn.example-app.net
```

- One domain per line; omit protocol prefixes (`http://`).
- Do not include wildcard characters (`*`, `?`); FortiGate does not expand them.
- If a host requires both domain- and path-level control, list the FQDN here and the specific URL in `url_list`.

## Maintaining `url_list`
Use `url_list` for indicators that require full URL matching (protocol and path).

```
# example urls
https://downloads.example-app.com/updates/
https://example-app.com/api/v1/ping
```

- One indicator per line; include protocol when a path is present.
- Use trailing slashes when FortiGate must match only inside a directory.
- Avoid query strings unless essential; FortiGate matches the literal string provided.

## Publishing the Feeds to FortiGate
1. Commit and push the updated lists.
2. In FortiGate, create separate external connectors under **Security Fabric → External Connectors → Create New**:
	- **URL Feed** pointing to `https://raw.githubusercontent.com/<org>/<repo>/main/external-threat-feeds/url_list`.
	- **Domain Feed** pointing to `https://raw.githubusercontent.com/<org>/<repo>/main/external-threat-feeds/domain_list`.
3. Enable the connectors and reference them in web filtering profiles, firewall policies, or automation stitches as required.

## Quality Checklist Before Commit
- Confirm indicators resolve and belong to the documented applications.
- Ensure `application_list` entries align with `domain_list` and `url_list`.
- Run `sort -u` locally to remove duplicates and verify FortiGate ingests the feeds without errors.