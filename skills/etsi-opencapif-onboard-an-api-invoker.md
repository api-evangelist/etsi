---
name: Onboard an API invoker with ETSI OpenCAPIF
description: >-
  Onboard, update and offboard an API invoker against ETSI OpenCAPIF — the ETSI SDG
  implementation of the 3GPP Common API Framework (TS 29.222) — and read the access control
  policy and invocation audit log that govern it.
api: openapi/capif/capif-api-invoker-management.yaml, openapi/capif/capif-api-provider-management.yaml,
  openapi/capif/capif-access-control-policy.yaml, openapi/capif/capif-auditing.yaml
operations:
  - create_onboarded_api_invoker
  - update_ind_onboarded_api_invoker
  - modify_ind_api_invoke_enrolment
  - delete_ind_onboarded_api_invoker
generated: '2026-07-25'
method: generated
source: openapi/capif/ (3GPP TS 29.222 as implemented by ETSI SDG OpenCAPIF)
---

# Onboard an API invoker with ETSI OpenCAPIF

CAPIF is 3GPP's Common API Framework — the northbound gate a mobile operator puts in front of its
network APIs. ETSI's OpenCAPIF Software Development Group ships the reference implementation.
This skill covers the invoker side: getting your application admitted so it can call operator APIs.

## Before you start

- Docs: <https://ocf.etsi.org/documentation/latest/> — code:
  <https://labs.etsi.org/rep/ocf/capif>
- There is a **first-party Python SDK**: `pip install opencapif-sdk`
  (<https://pypi.org/project/opencapif-sdk/>, source at <https://labs.etsi.org/rep/ocf/sdk>).
  Prefer it over hand-rolling the certificate and token dance.
- Authorization is **OAuth 2.0 client credentials**. The token URL is a deployment template
  (`{tokenUrl}`) — the CAPIF core function tells you the real one during onboarding.
- Errors are RFC 7807/9457 `ProblemDetails` on `application/problem+json`.
- Base path: `{apiRoot}/api-invoker-management/v1`.

## Steps

1. **Onboard.** `create_onboarded_api_invoker` — `POST /onboardedInvokers` with an
   `APIInvokerEnrolmentDetails` body: your `notificationDestination`, the
   `onboardingInformation.apiInvokerPublicKey` (the CAPIF core signs it and returns your invoker
   certificate), and `apiList` if you already know which service APIs you want. The response
   carries your `apiInvokerId` and the signed certificate — **this is the credential everything
   else depends on.**
2. **Keep it current.** `update_ind_onboarded_api_invoker` —
   `PUT /onboardedInvokers/{onboardingId}` for a full replacement of the enrolment, or
   `modify_ind_api_invoke_enrolment` — `PATCH /onboardedInvokers/{onboardingId}` for a partial
   change (adding an API to `apiList`, rotating the notification destination).
3. **Check what you are allowed to call.** The Access Control Policy API
   (`openapi/capif/capif-access-control-policy.yaml`) returns the per-invoker, per-service policy
   the CAPIF core will enforce — including any rate limits and time-window restrictions. Read it
   before you assume an operation will succeed.
4. **Audit your own invocations.** The CAPIF Auditing API
   (`openapi/capif/capif-auditing.yaml`) exposes the invocation log. Use it to reconcile what you
   think you called with what the operator recorded.
5. **Offboard.** `delete_ind_onboarded_api_invoker` —
   `DELETE /onboardedInvokers/{onboardingId}`. This revokes the invoker certificate. Do it when
   you decommission the application rather than leaving a live credential behind.

## Notes

- The **provider** side is symmetric: `openapi/capif/capif-api-provider-management.yaml` is what
  an API exposing function uses to register itself with the same CAPIF core. Onboarding an
  invoker and registering a provider are two halves of the same framework.
- No idempotency key. `create_onboarded_api_invoker` on an invoker you already onboarded creates
  a second enrolment — check first, do not blind-retry.

## Failure modes

| Status | Meaning |
|---|---|
| 400 | malformed enrolment body, or an unusable public key |
| 401 | missing or expired client-credentials token |
| 403 | the CAPIF core's access control policy forbids this |
| 404 | unknown `onboardingId` — you may already be offboarded |
| 411 / 413 / 414 / 415 | CAPIF is strict about Content-Length, body size, URI length and media type |
| 429 | rate limited by the CAPIF core |
