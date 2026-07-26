---
name: Manage context entities with the ETSI NGSI-LD API
description: >-
  Create, query, update and subscribe to context entities in an ETSI NGSI-LD context broker
  (ETSI GS CIM 009), including JSON-LD @context handling, temporal queries and federating across
  registered context sources.
api: openapi/ngsi-ld/ngsi-ld-api-3.1.0.yaml
operations:
  - createEntity
  - queryEntity
  - retrieveEntity
  - mergeEntity
  - replaceEntity
  - updateEntity
  - appendAttrs
  - updateAttrs
  - replaceAttrs
  - deleteAttrs
  - deleteEntity
  - createSubscription
  - querySubscription
  - retrieveSubscription
  - updateSubscription
  - deleteSubscription
  - createCSR
  - queryCSR
  - retrieveCSR
  - updateCSR
  - deleteCSR
generated: '2026-07-25'
method: generated
source: openapi/ngsi-ld/ngsi-ld-api-3.1.0.yaml (ETSI ISG CIM, GS CIM 009)
---

# Manage context entities with the ETSI NGSI-LD API

NGSI-LD is ETSI ISG CIM's JSON-LD context information management API — the API layer beneath most
European smart-city and FIWARE deployments. Base path is `{apiRoot}/ngsi-ld/v1`.

## Before you start

- **The `@context` is not optional.** Every entity, attribute and query is interpreted against a
  JSON-LD `@context`. Send it either inline in the body (`Content-Type: application/ld+json`) or
  in a `Link` header with `rel="http://www.w3.org/ns/json-ld#context"` when using
  `application/json`. Getting this wrong is the single most common NGSI-LD failure.
- Entity `id` is a URI (`urn:ngsi-ld:Building:store001`), and `type` is a term resolved through
  the `@context`.
- Attributes are either a **Property** (has `value`) or a **Relationship** (has `object`, a URI
  pointing at another entity). That distinction drives everything else.
- No security scheme is declared in the specification — the broker deployment supplies one.
- Errors are RFC 7807/9457 `ProblemDetails` with NGSI-LD problem types
  (`InvalidRequest`, `BadRequestData`, `AlreadyExists`, `ResourceNotFound`, `OperationNotSupported`).
- There is no idempotency key. `createEntity` on an existing `id` returns **409 AlreadyExists** —
  that is your idempotency check.

## Steps

1. **Create an entity.** `createEntity` — `POST /entities`. Body carries `id`, `type`, your
   Properties and Relationships, and the `@context`. 201 on success, 409 if the id exists.
2. **Query.** `queryEntity` — `GET /entities?type=Building&q=temperature>25&limit=100`. Combine
   `type`, `attrs`, `q` (the NGSI-LD query language), `georel`/`geometry`/`coordinates` for
   geo-queries, and `options=keyValues` for a flattened response.
3. **Read one.** `retrieveEntity` — `GET /entities/{entityId}?attrs=temperature,humidity`.
4. **Update.** Pick the right verb — NGSI-LD distinguishes five:
   - `updateEntity` — `PATCH /entities/{entityId}/attrs` — partial update of existing attributes.
   - `appendAttrs` — `POST /entities/{entityId}/attrs` — add attributes (with
     `options=noOverwrite` to refuse clobbering).
   - `mergeEntity` — `PATCH /entities/{entityId}` — JSON-merge semantics over the whole entity.
   - `replaceEntity` — `PUT /entities/{entityId}` — full replacement.
   - `updateAttrs` / `replaceAttrs` — `PATCH` / `PUT /entities/{entityId}/attrs/{attrId}` — one
     attribute at a time.
5. **Delete.** `deleteAttrs` — `DELETE /entities/{entityId}/attrs/{attrId}` for one attribute, or
   `deleteEntity` — `DELETE /entities/{entityId}` for the whole thing.
6. **Subscribe to change.** `createSubscription` — `POST /subscriptions` with `entities[]`
   (by `type`, `id` or `idPattern`), `watchedAttributes`, an optional `q` condition, and a
   `notification.endpoint.uri`. Manage with `querySubscription`, `retrieveSubscription`,
   `updateSubscription`, `deleteSubscription`.
7. **Federate.** `createCSR` — `POST /csourceRegistrations` registers another context source with
   this broker so queries fan out to it. `queryCSR`, `retrieveCSR`, `updateCSR`, `deleteCSR`
   manage the registrations. This is how NGSI-LD does distributed context without a central store.

## Version note

Two documents are harvested here: `ngsi-ld-api-3.0.3.yaml` and `ngsi-ld-api-3.1.0.yaml`. Check
which the broker implements before assuming an operation exists — 3.1.0 added operations the
3.0.3 line does not carry.

## Failure modes

| Status | NGSI-LD problem type | Cause |
|---|---|---|
| 400 | `BadRequestData` / `InvalidRequest` | usually a missing or unresolvable `@context` term |
| 404 | `ResourceNotFound` | unknown entity, attribute or subscription id |
| 409 | `AlreadyExists` | `createEntity` on an existing id |
| 422 | `OperationNotSupported` | the broker does not implement this optional operation |
| 501 | not implemented | the broker predates this part of the specification |
