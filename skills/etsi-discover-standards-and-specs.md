---
name: Find an ETSI standard and its machine-readable OpenAPI
description: >-
  Locate any ETSI deliverable and, where one exists, the BSD-3-Clause OpenAPI that goes with it —
  using the free standards library, the anonymous ETSI Forge and ETSI Labs GitLab REST APIs, and
  the public work programme.
api: https://forge.etsi.org/rep/api/v4, https://labs.etsi.org/rep/api/v4
base_url: https://forge.etsi.org/rep/api/v4
operations: []
generated: '2026-07-25'
method: generated
source: live probes of forge.etsi.org/rep/api/v4 and labs.etsi.org/rep/api/v4
---

# Find an ETSI standard and its machine-readable OpenAPI

ETSI is unusual among standards bodies: **the finished standards and their OpenAPI are free and
open to anyone.** Membership gates participation (drafting, voting, working documents on
portal.etsi.org), not publication. This skill is the discovery path.

## The four surfaces

| What | Where | Auth |
|---|---|---|
| Every deliverable, as PDF | <https://www.etsi.org/deliver/> | none, no login |
| Standards by technology | <https://www.etsi.org/standards/get-standards> | none |
| OpenAPI for MEC, NFV SOL, NGSI-LD | <https://forge.etsi.org/rep/> (GitLab) | anonymous read |
| OpenAPI + code for OpenCAPIF, OpenSlice, Operator Platform, TeraFlowSDN | <https://labs.etsi.org/rep/> (GitLab) | anonymous read |
| Work in progress (the de-facto roadmap) | <https://portal.etsi.org/webapp/WorkProgram/> | none |

## Steps

1. **List the groups.** `GET https://forge.etsi.org/rep/api/v4/groups?per_page=100` — returns the
   technical bodies that publish to Forge: `mec`, `nfv`, `cim`, `cyber`, `esi`, `ITS`, `li`,
   `3GPP`, `f5g` and dozens more. No token needed.
2. **List a group's projects.**
   `GET https://forge.etsi.org/rep/api/v4/groups/mec/projects?per_page=50`. Project paths follow
   the deliverable number — `mec/gs011-app-enablement-api`, `mec/gs013-location-api`,
   `nfv/SOL005`, `cim/ngsi-ld-openapi`.
3. **Find the right version.**
   `GET https://forge.etsi.org/rep/api/v4/projects/mec%2Fgs011-app-enablement-api/repository/tags`
   — tags are the ETSI deliverable version, `V<major>.<technical>.<editorial>`. URL-encode the
   `/` in the project path as `%2F`.
4. **Read the tree.**
   `GET https://forge.etsi.org/rep/api/v4/projects/<path>/repository/tree?ref=<tag>` then fetch
   the file you want. The OpenAPI is BSD-3-Clause
   (<https://forge.etsi.org/legal-matters>).
5. **Read the prose standard.** The OpenAPI is normative-adjacent, not self-explaining. Pull the
   matching PDF from <https://www.etsi.org/deliver/> — free, no account.
6. **Check what is coming.** The ETSI Work Programme at
   <https://portal.etsi.org/webapp/WorkProgram/> lists every work item with its stage, target
   date and responsible technical body.

## Try it live before you build

- **ETSI MEC Sandbox** — <https://try-mec.etsi.org/> — free, account required, real MEC 011/012/
  013/021/028/030/040 APIs against emulated 4G/5G/Wi-Fi networks with moving UEs.
- **ETSI OpenSlice demo** — `https://portal.openslice.eu/tmf-api` — 25 live TM Forum Open APIs,
  reads answer anonymously. The spec index is at
  `https://portal.openslice.eu/tmf-api/v3/api-docs/swagger-config`.

## For agents

Both GitLab instances run an MCP server — `https://forge.etsi.org/rep/api/v4/mcp` and
`https://labs.etsi.org/rep/api/v4/mcp` — advertised in RFC 9728 protected-resource metadata at
`/.well-known/oauth-protected-resource`. They need an OAuth token with the `mcp` scope; anonymous
`tools/list` returns 401. See `mcp/etsi-mcp.yml`.

## Gotcha

The `servers[]` block in most ETSI OpenAPI documents is `{apiRoot}` or `127.0.0.1` **by design** —
these describe a standardised interface, not a hosted service. The only production host in the
whole corpus is `https://portal.openslice.eu/tmf-api`. Do not treat a loopback server URL as a
broken spec.
