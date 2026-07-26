---
name: Order a network service from the ETSI OpenSlice catalog
description: >-
  Browse the ETSI OpenSlice TM Forum service catalog, pick a service specification, place a
  service order for it, and track the order and the resulting service through to activation.
api: openapi/openslice-tmf/tmf-api-633-ServiceCatalogManagement-v4.0.0.json,
  openapi/openslice-tmf/tmf-api-641-ServiceOrdering-v4.0.0.json,
  openapi/openslice-tmf/tmf-api-638-ServiceInventoryManagement-v4.0.0.json
base_url: https://portal.openslice.eu/tmf-api
operations:
  - listServiceCatalog
  - listServiceCategory
  - listServiceCandidate
  - listServiceSpecification
  - retrieveServiceSpecification
  - createServiceOrder
  - retrieveServiceOrder
  - listService
  - retrieveService
  - registerListener
generated: '2026-07-25'
method: generated
source: openapi/openslice-tmf/ (harvested live from https://portal.openslice.eu/tmf-api/v3/api-docs)
---

# Order a network service from the ETSI OpenSlice catalog

ETSI OpenSlice is an open-source service-based OSS that delivers Network as a Service through the
TM Forum Open APIs. This skill walks the catalog → order → inventory path on a real ETSI
deployment.

## Before you start

- Base URL: `https://portal.openslice.eu/tmf-api`
- The public ETSI demo answers **read** paths anonymously. Writes need an OAuth 2.0 bearer token
  from `https://portal.openslice.eu/auth/realms/openslice` (authorization code flow, scopes
  `read` and `write`). See `authentication/etsi-authentication.yml`.
- Errors use the TM Forum envelope (`code`, `reason`, `message`, `status`, `referenceError`) on
  `application/json;charset=utf-8`, **not** RFC 9457. See `errors/etsi-problem-types.yml`.
- There is **no idempotency key** in this API. Do not blind-retry `createServiceOrder` — re-read
  with `listServiceOrder` first, or you will create duplicate orders.
- List operations paginate with `offset` and `limit`, and accept a `fields` query parameter for
  sparse responses.

## Steps

1. **Find the catalog.** `listServiceCatalog` — `GET /serviceCatalogManagement/v4/serviceCatalog`.
   Take the catalog `id` you want to shop from.
2. **Walk the categories.** `listServiceCategory` — `GET /serviceCatalogManagement/v4/serviceCategory`.
   Categories hold service candidates.
3. **List the candidates.** `listServiceCandidate` — `GET /serviceCatalogManagement/v4/serviceCandidate`.
   Each candidate points at a `serviceSpecification`.
4. **List or search specifications directly.** `listServiceSpecification` —
   `GET /serviceCatalogManagement/v4/serviceSpecification?limit=20`. Filter on
   `lifecycleStatus` to skip anything still `In study`.
5. **Read the specification you picked.** `retrieveServiceSpecification` —
   `GET /serviceCatalogManagement/v4/serviceSpecification/{id}`. Read
   `serviceSpecCharacteristic` — those are the parameters your order must supply.
6. **Place the order.** `createServiceOrder` — `POST /serviceOrdering/v4/serviceOrder`. The body
   carries `serviceOrderItem[]`, each with an `action` (`add`), a `service.serviceSpecification`
   reference back to step 5, and `service.serviceCharacteristic` values matching the
   characteristics you read.
7. **Track the order.** `retrieveServiceOrder` — `GET /serviceOrdering/v4/serviceOrder/{id}`.
   Watch `state` move through `acknowledged` → `inProgress` → `completed`.
8. **Find the realised service.** `listService` — `GET /serviceInventory/v4/service`, then
   `retrieveService` — `GET /serviceInventory/v4/service/{id}` for the running instance.

## Instead of polling

Register a webhook rather than looping on step 7:

- `registerListener` — `POST /serviceOrdering/v4/hub` with `{"callback": "<your https URL>"}`.
- OpenSlice then POSTs to your listener at `/serviceOrdering/v4/listener/serviceOrderStateChangeNotification`
  and `/serviceOrdering/v4/listener/serviceOrderAttributeValueChangeNotification`.
- `unregisterListener` — `DELETE /serviceOrdering/v4/hub/{id}` when you are done.

See `asyncapi/etsi-webhooks.yml` for the full event catalog (146 TM Forum notification types).

## Failure modes

| Status | What it means here | What to do |
|---|---|---|
| 400 | order body does not match the specification's characteristics | re-read step 5 |
| 401 | no bearer token on a write | get a token from the Keycloak realm |
| 403 | token lacks the `write` scope | re-authorize with `write` |
| 404 | wrong `id`, or wrong TMF version in the path | check `/v4` vs `/v3` vs `/v5` per TMF number |
| 409 | the order or service is in a state that forbids the change | re-read state, then retry |
| 501 | this deployment did not implement an optional TMF operation | treat as a capability signal |
