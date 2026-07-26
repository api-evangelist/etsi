---
name: Register and discover services on an ETSI MEC platform
description: >-
  Use the ETSI GS MEC 011 Mp1 reference point to register a MEC application with the platform,
  publish a service, discover other services, subscribe to availability changes, and terminate
  cleanly.
api: openapi/mec/MecServiceMgmtApi.yaml, openapi/mec/MecAppSupportApi.yaml
operations:
  - RegistrationsPOST
  - ApplicationsConfirmreadyPOSTAppinstanceid
  - ApplicationsServicesPOSTAppinstanceid
  - ServicesGET
  - ServicesGETServiceid
  - TransportsGET
  - ApplicationsServicesGETAppinstanceid
  - ApplicationsServicesPUTAppinstanceidServiceid
  - ApplicationsSubscriptionsPOSTAppinstanceid
  - ApplicationsSubscriptionsGETAppinstanceid
  - ApplicationsSubscriptionsDELETEAppinstanceidSubscriptionid
  - ApplicationsTrafficrulesGETAppinstanceid
  - ApplicationsDnsrulesGETAppinstanceid
  - ApplicationsConfirmterminationPOSTAppinstanceid
  - ApplicationsServicesDELETEAppinstanceidServiceid
generated: '2026-07-25'
method: generated
source: openapi/mec/MecServiceMgmtApi.yaml, openapi/mec/MecAppSupportApi.yaml (ETSI GS MEC 011)
---

# Register and discover services on an ETSI MEC platform

ETSI GS MEC 011 defines Mp1, the reference point between a MEC application and the MEC platform.
This is the flow every edge application follows on start-up.

## Before you start

- Base URL is deployment-specific: `{apiRoot}/mec_app_support/v2` and `{apiRoot}/mec_service_mgmt/v2`.
  ETSI does not host a production MEC platform — try it against the **ETSI MEC Sandbox** at
  <https://try-mec.etsi.org/> (free, account required). See `sandbox/etsi-sandbox.yml`.
- MEC 011 declares no security scheme in the specification. The deployment supplies one
  (MEC 009 recommends OAuth 2.0 client credentials).
- Errors are RFC 7807/9457 `ProblemDetails` on `application/problem+json`.
- Modifying a service uses `ETag` / `If-Match` for optimistic concurrency. A 412 means someone
  else changed it — re-read and retry.
- There is no idempotency key. Registration is naturally idempotent by `appInstanceId`; service
  publication is not.

## Steps

1. **Register the application.** `RegistrationsPOST` — `POST /registrations` with your
   `AppInfo`. The platform returns the registration and your `appInstanceId`.
2. **Confirm you are ready.** `ApplicationsConfirmreadyPOSTAppinstanceid` —
   `POST /applications/{appInstanceId}/confirm_ready`. Until you do this the platform will not
   consider the instance operational.
3. **Check available transports.** `TransportsGET` — `GET /transports`. Publish on a transport
   the platform actually offers (REST_HTTP, MB_TOPIC_BASED, ...).
4. **Publish your own service.** `ApplicationsServicesPOSTAppinstanceid` —
   `POST /applications/{appInstanceId}/services` with a `ServiceInfo` (name, version, state,
   transport, serializer, scope of locality). The platform assigns `serInstanceId`.
5. **Discover other services.** `ServicesGET` — `GET /services`, filtered by `ser_name`,
   `ser_category_id` or `consumed_local_only`. Then `ServicesGETServiceid` —
   `GET /services/{serviceId}` for the full record including its endpoint.
6. **Subscribe to availability changes.** `ApplicationsSubscriptionsPOSTAppinstanceid` —
   `POST /applications/{appInstanceId}/subscriptions` with a `SerAvailabilityNotificationSubscription`
   carrying your `callbackReference`. The platform POSTs a notification whenever a service you
   care about appears, changes state or disappears.
7. **Read the rules the platform applied to you.**
   `ApplicationsTrafficrulesGETAppinstanceid` — `GET /applications/{appInstanceId}/traffic_rules`
   and `ApplicationsDnsrulesGETAppinstanceid` — `GET /applications/{appInstanceId}/dns_rules`.
   Activate a rule by PUTting it back with `state: ACTIVE`.
8. **Keep your service record current.** `ApplicationsServicesPUTAppinstanceidServiceid` —
   `PUT /applications/{appInstanceId}/services/{serviceId}` with the `If-Match` ETag you read.

## Shutting down cleanly

1. `ApplicationsSubscriptionsDELETEAppinstanceidSubscriptionid` —
   `DELETE /applications/{appInstanceId}/subscriptions/{subscriptionId}` for each subscription.
2. `ApplicationsServicesDELETEAppinstanceidServiceid` —
   `DELETE /applications/{appInstanceId}/services/{serviceId}`.
3. `ApplicationsConfirmterminationPOSTAppinstanceid` —
   `POST /applications/{appInstanceId}/confirm_termination` so the platform can reclaim the
   instance instead of waiting out its grace timer.

## Failure modes

| Status | Meaning | Action |
|---|---|---|
| 400 | malformed `ServiceInfo` or bad filter | check the MEC 011 schema |
| 403 | operation not permitted for this app instance | check the platform's app policy |
| 404 | unknown `appInstanceId` or `serviceId` | re-register (step 1) |
| 412 | `If-Match` ETag stale | re-read the resource, retry with the new ETag |
| 429 | platform is rate limiting | back off; no RateLimit header contract is defined |
