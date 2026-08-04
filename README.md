# ETSI (etsi)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

ETSI, the European Telecommunications Standards Institute, is a not-for-profit standards development organisation headquartered in Sophia Antipolis, France, and one of only three bodies officially recognised by the European Union as a European Standards Organisation. With over 900 member organisations from more than 60 countries it standardises ICT across mobile, fixed, broadcast, IoT, security and emerging technologies, and it hosts the 3GPP Mobile Competence Centre. In the telecom value chain ETSI sits upstream of every operator and vendor: it does not run a network or sell connectivity, it writes the specifications that the network is built from. Its API posture is unusually open for a standards body. Every ETSI deliverable is downloadable free of charge without login from etsi.org/deliver, and the machine-readable API artefacts are published as BSD-3-Clause OpenAPI on two public GitLab instances, forge.etsi.org and labs.etsi.org, both of which serve an anonymous REST API. From those ETSI publishes the ISG MEC edge service APIs, the NFV SOL lifecycle and orchestration APIs, the ISG CIM NGSI-LD context information API, and open-source implementations including OpenCAPIF for 3GPP CAPIF, OpenSlice for TM Forum Open APIs, and an Operator Platform Open Exposure Gateway that exposes northbound CAMARA APIs. What is member-gated is participation, not publication: portal.etsi.org, working documents, drafting and voting sit behind ETSI membership, while the finished standards and their OpenAPI are open to anyone. ETSI itself is not a GSMA Open Gateway operator and not a CAMARA member organisation; it reaches CAMARA through liaison and through its own open-source code.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/etsi/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/etsi/refs/heads/main/apis.yml)

## Tags

- Telecommunications
- France
- Standards
- Standards Body
- Network APIs
- Edge Computing
- MEC
- NFV
- 5G
- CAMARA
- TM Forum
- 3GPP
- CAPIF
- NGSI-LD
- IoT
- Open Source
- Europe
- OpenAPI
- Network Slicing
- Broadband

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## What Is Open, What Is Gated

ETSI's specifications are free. Every ETSI deliverable downloads anonymously from [etsi.org/deliver](https://www.etsi.org/deliver/) with no login, no paywall and no email capture — a direct fetch of ETSI GS MEC 011 v3.2.1 returned HTTP 200 and 4.5 MB of PDF. The machine-readable artefacts live in source control on two public GitLab instances, [forge.etsi.org](https://forge.etsi.org/rep/) (62 groups, 284 projects) and [labs.etsi.org](https://labs.etsi.org/rep/) (41 groups, 160 projects), both of which answer an anonymous `/api/v4` REST API and both licensed [BSD-3-Clause](https://forge.etsi.org/legal-matters).

What is gated is participation, not publication. [portal.etsi.org](https://portal.etsi.org/) — the work programme, drafting and voting — is for ETSI's 900+ member organisations. The hosted [MEC Sandbox](https://try-mec.etsi.org/) is free but account-gated: its web front end loads anonymously while its API paths return HTTP 401 until you sign in.

There is no `developer.etsi.org`, `developers.etsi.org` or `docs.etsi.org` — none of those hosts resolve, and `api.etsi.org` answers only 404. ETSI publishes OpenAPI from git, not from a docs portal.

## CAMARA, GSMA and TM Forum Posture

ETSI sits **upstream** of CAMARA. CAMARA defines its Service APIs as an abstraction over 3GPP, Broadband Forum and ETSI MEC APIs, so ETSI supplies raw material rather than consuming it. ETSI is **not** a GSMA Open Gateway participant (it operates no network) and reaches no market through Aduna or any CPaaS channel — it has no commercial API channel at all.

But this is not a press-release relationship. Two callable CAMARA-shaped OpenAPI documents were harvested from ETSI's own repositories: a **CAMARA Quality on Demand (QoD) Provisioning API** in the OpenSlice CAMARAaaS add-on, and the **Operator Platform Open Exposure Gateway**, which implements the northbound CAMARA Edge Cloud Management, Network Exposure (QoD sessions and device location retrieval) and Federation Management APIs, filling the Open Exposure Gateway role defined by the GSMA Operator Platform Group. CAMARA APIs with real evidence here: **Quality on Demand, Device Location, Edge Cloud / Application Management, Traffic Influence, Federation Management**. Not found: Number Verification, SIM Swap, Device Status, Carrier Billing, KYC Match, Scam Signal, Device Swap, Population Density.

On **TM Forum**: ETSI holds no Open API conformance certification, but ETSI SDG OpenSlice implements and documents more than twenty TM Forum Open APIs (TMF620, TMF622, TMF629, TMF632, TMF633, TMF634, TMF638, TMF639, TMF640, TMF641, TMF642, TMF651, TMF652, TMF653, TMF657, TMF666, TMF669, TMF685, TMF691), and the public OpenSlice demo answers them anonymously.

On **3GPP**: ETSI hosts the 3GPP Mobile Competence Centre, and ETSI SDG OpenCAPIF is an open-source implementation of the 3GPP Common API Framework (TS 29.222) whose service APIs are harvested here.

## Authentication

Mixed, and mostly unspecified by design. The CAMARA QoD Provisioning API declares **OpenID Connect** plus HTTP Bearer for notification sinks; OpenCAPIF declares **OAuth 2.0 client credentials**; NFV SOL002/SOL003 define `OAUTH2_CLIENT_CREDENTIALS`, `BASIC` and `TLS_CERT` as notification-endpoint auth types. **CIBA does not appear anywhere** — a recursive search across all 159 harvested files found no `ciba` or `backchannel` reference. The ETSI MEC and NGSI-LD documents declare no security schemes at all and carry placeholder servers (`127.0.0.1`, `localhost:8081`), which is the correct shape for specification-grade contracts meant to be implemented rather than called.

## Harvested Specifications

**87 valid OpenAPI documents, 730 operations, 159 files** saved verbatim under `openapi/` with provenance recorded in `review.yml`. Sources: ETSI ISG MEC (17 specs), ETSI ISG NFV SOL002/003/005/009/011/012 (62 specs, full `src/` trees preserved so relative `$ref` targets resolve), ETSI ISG CIM NGSI-LD (2), ETSI SDG OpenCAPIF (4) and ETSI's two CAMARA-shaped APIs (2).

## APIs

### ETSI MEC 011 Edge Platform Application Enablement API

The Mp1 reference point between MEC applications and the MEC platform, standardised in ETSI GS MEC 011. Covers MEC service registration, deregistration, discovery and event notification (MecServiceMgmtApi) plus application start-up, traffic rules, DNS rules, time-of-day and termination support (MecAppSupportApi). Published as OpenAPI 3.1.0 under BSD-3-Clause on the public ETSI Forge GitLab.

- **Human URL:** [https://forge.etsi.org/rep/mec/gs011-app-enablement-api](https://forge.etsi.org/rep/mec/gs011-app-enablement-api)

#### Tags

- Edge Computing
- MEC
- Service Discovery
- 5G

#### Properties

- [Documentation](https://www.etsi.org/technologies/multi-access-edge-computing)
- [APIReference](https://forge.etsi.org/rep/mec/gs011-app-enablement-api)
- [Repository](https://forge.etsi.org/rep/mec/gs011-app-enablement-api)
- [OpenAPI](openapi/mec/MecServiceMgmtApi.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [OpenAPI](openapi/mec/MecAppSupportApi.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI MEC 012 Radio Network Information API

The Radio Network Information Service (RNIS) defined in ETSI GS MEC 012, exposing up-to-date radio network conditions, measurement reports, cell change and carrier aggregation information from the RAN to authorised MEC applications so edge software can adapt to real network state.

- **Human URL:** [https://forge.etsi.org/rep/mec/gs012-rnis-api](https://forge.etsi.org/rep/mec/gs012-rnis-api)

#### Tags

- Edge Computing
- MEC
- Radio Network
- 5G

#### Properties

- [Documentation](https://www.etsi.org/technologies/multi-access-edge-computing)
- [APIReference](https://forge.etsi.org/rep/mec/gs012-rnis-api)
- [Repository](https://forge.etsi.org/rep/mec/gs012-rnis-api)
- [OpenAPI](openapi/mec/RniAPI.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI MEC 013 Location API

The MEC Location Service defined in ETSI GS MEC 013, providing network-derived location of user equipment and of radio nodes, zone and access-point occupancy, distance calculation, area and periodic location subscriptions. It is the ETSI edge-side analogue of the network location capability that CAMARA exposes commercially as Device Location.

- **Human URL:** [https://forge.etsi.org/rep/mec/gs013-location-api](https://forge.etsi.org/rep/mec/gs013-location-api)

#### Tags

- Edge Computing
- MEC
- Location
- Geolocation

#### Properties

- [Documentation](https://www.etsi.org/technologies/multi-access-edge-computing)
- [APIReference](https://forge.etsi.org/rep/mec/gs013-location-api)
- [Repository](https://forge.etsi.org/rep/mec/gs013-location-api)
- [OpenAPI](openapi/mec/LocationAPI.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI MEC 014 UE Identity API

The UE Identity API from ETSI GS MEC 014, which lets a MEC application register a UE identity tag with the MEC platform so that traffic filtering rules can be applied to a specific device.

- **Human URL:** [https://forge.etsi.org/rep/mec/gs014-ue-identity-api](https://forge.etsi.org/rep/mec/gs014-ue-identity-api)

#### Tags

- Edge Computing
- MEC
- Identity

#### Properties

- [Documentation](https://www.etsi.org/technologies/multi-access-edge-computing)
- [APIReference](https://forge.etsi.org/rep/mec/gs014-ue-identity-api)
- [Repository](https://forge.etsi.org/rep/mec/gs014-ue-identity-api)
- [OpenAPI](openapi/mec/UEidentityAPI.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI MEC 015 Traffic Management APIs

The two traffic-management APIs of ETSI GS MEC 015: Bandwidth Management, which lets applications register bandwidth requirements and priorities with the MEC platform, and Multi-access Traffic Steering, which configures how sessions are steered across multiple access networks.

- **Human URL:** [https://forge.etsi.org/rep/mec/gs015-bandwith-mgmt-api](https://forge.etsi.org/rep/mec/gs015-bandwith-mgmt-api)

#### Tags

- Edge Computing
- MEC
- Traffic Management
- Bandwidth

#### Properties

- [Documentation](https://www.etsi.org/technologies/multi-access-edge-computing)
- [APIReference](https://forge.etsi.org/rep/mec/gs015-bandwith-mgmt-api)
- [Repository](https://forge.etsi.org/rep/mec/gs015-bandwith-mgmt-api)
- [OpenAPI](openapi/mec/BwManagementApi.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [OpenAPI](openapi/mec/TrafficSteeringApi.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI MEC 016 UE Application Interface API

The Mx2 reference point from ETSI GS MEC 016, used by a device-side application to discover which MEC applications are available in the system and to request instantiation or termination of a user application in the edge cloud.

- **Human URL:** [https://forge.etsi.org/rep/mec/gs016-dev-app-api](https://forge.etsi.org/rep/mec/gs016-dev-app-api)

#### Tags

- Edge Computing
- MEC
- Application Lifecycle

#### Properties

- [Documentation](https://www.etsi.org/technologies/multi-access-edge-computing)
- [APIReference](https://forge.etsi.org/rep/mec/gs016-dev-app-api)
- [Repository](https://forge.etsi.org/rep/mec/gs016-dev-app-api)
- [OpenAPI](openapi/mec/UEAppInterfaceApi.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI MEC 010-2 Application Package and Lifecycle Management APIs

ETSI GS MEC 010-2 Part 2 application package management, application lifecycle management and application grant APIs, used by an operations support system to onboard, instantiate, operate and terminate MEC application packages in a MEC system.

- **Human URL:** [https://forge.etsi.org/rep/mec/gs010-2-app-pkg-lcm-api](https://forge.etsi.org/rep/mec/gs010-2-app-pkg-lcm-api)

#### Tags

- Edge Computing
- MEC
- Application Lifecycle
- Orchestration

#### Properties

- [Documentation](https://www.etsi.org/technologies/multi-access-edge-computing)
- [APIReference](https://forge.etsi.org/rep/mec/gs010-2-app-pkg-lcm-api)
- [Repository](https://forge.etsi.org/rep/mec/gs010-2-app-pkg-lcm-api)
- [OpenAPI](openapi/mec/MEC01002_AppPkgMgmt.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [OpenAPI](openapi/mec/MEC01002_AppLcm.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [OpenAPI](openapi/mec/MEC01002_AppGrant.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI MEC 021 Application Mobility Service API

The Application Mobility Service defined in ETSI GS MEC 021, which coordinates the relocation of a running application instance and its user context between MEC hosts as a device moves across the network.

- **Human URL:** [https://forge.etsi.org/rep/mec/gs021-amsi-api](https://forge.etsi.org/rep/mec/gs021-amsi-api)

#### Tags

- Edge Computing
- MEC
- Mobility

#### Properties

- [Documentation](https://www.etsi.org/technologies/multi-access-edge-computing)
- [APIReference](https://forge.etsi.org/rep/mec/gs021-amsi-api)
- [Repository](https://forge.etsi.org/rep/mec/gs021-amsi-api)
- [OpenAPI](openapi/mec/MEC021_AppMobilityService.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI MEC 028 WLAN Information API

The WLAN Access Information Service from ETSI GS MEC 028, exposing access-point, station and measurement information from Wi-Fi networks to edge applications alongside the cellular information services.

- **Human URL:** [https://forge.etsi.org/rep/mec/gs028-wai-api](https://forge.etsi.org/rep/mec/gs028-wai-api)

#### Tags

- Edge Computing
- MEC
- WLAN
- Wi-Fi

#### Properties

- [Documentation](https://www.etsi.org/technologies/multi-access-edge-computing)
- [APIReference](https://forge.etsi.org/rep/mec/gs028-wai-api)
- [Repository](https://forge.etsi.org/rep/mec/gs028-wai-api)
- [OpenAPI](openapi/mec/WlanInformationApi.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI MEC 029 Fixed Access Information API

The Fixed Access Information Service from ETSI GS MEC 029, extending MEC information exposure beyond mobile to fixed broadband access networks including PON and cable, so edge applications can read fixed-line network conditions.

- **Human URL:** [https://forge.etsi.org/rep/mec/gs029-fai-api](https://forge.etsi.org/rep/mec/gs029-fai-api)

#### Tags

- Edge Computing
- MEC
- Broadband
- Fixed Access

#### Properties

- [Documentation](https://www.etsi.org/technologies/multi-access-edge-computing)
- [APIReference](https://forge.etsi.org/rep/mec/gs029-fai-api)
- [Repository](https://forge.etsi.org/rep/mec/gs029-fai-api)
- [OpenAPI](openapi/mec/MEC029_FAI.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI MEC 030 V2X Information Services API

The V2X Information Service defined in ETSI GS MEC 030, providing predicted quality of service, provisioning information and multi-operator V2X message distribution for connected-vehicle applications running at the edge.

- **Human URL:** [https://forge.etsi.org/rep/mec/gs030-vis-api](https://forge.etsi.org/rep/mec/gs030-vis-api)

#### Tags

- Edge Computing
- MEC
- V2X
- Automotive

#### Properties

- [Documentation](https://www.etsi.org/technologies/multi-access-edge-computing)
- [APIReference](https://forge.etsi.org/rep/mec/gs030-vis-api)
- [Repository](https://forge.etsi.org/rep/mec/gs030-vis-api)
- [OpenAPI](openapi/mec/MEC030_V2XInformationServices.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI MEC 033 IoT API

The IoT API from ETSI GS MEC 033, defining how IoT device registration, IoT platform selection and device-to-platform association are managed by a MEC system so that IoT traffic can be terminated and processed at the edge.

- **Human URL:** [https://forge.etsi.org/rep/mec/gs033-iot-api](https://forge.etsi.org/rep/mec/gs033-iot-api)

#### Tags

- Edge Computing
- MEC
- IoT

#### Properties

- [Documentation](https://www.etsi.org/technologies/multi-access-edge-computing)
- [APIReference](https://forge.etsi.org/rep/mec/gs033-iot-api)
- [Repository](https://forge.etsi.org/rep/mec/gs033-iot-api)
- [OpenAPI](openapi/mec/MEC033_IoT.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI MEC 040 MEC Federation Enablement API

The MEC Federation enablement API from ETSI GS MEC 040, which lets edge systems operated by different providers discover one another, exchange availability zone and system information, and federate so an application can run across operator boundaries.

- **Human URL:** [https://forge.etsi.org/rep/mec/gs040-fed-enablement-api](https://forge.etsi.org/rep/mec/gs040-fed-enablement-api)

#### Tags

- Edge Computing
- MEC
- Federation

#### Properties

- [Documentation](https://www.etsi.org/technologies/multi-access-edge-computing)
- [APIReference](https://forge.etsi.org/rep/mec/gs040-fed-enablement-api)
- [Repository](https://forge.etsi.org/rep/mec/gs040-fed-enablement-api)
- [OpenAPI](openapi/mec/MEC040_fedEnablement.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI NFV SOL002 / SOL003 VNF Lifecycle, Fault, Performance and Package Management APIs

The RESTful protocols and data models of ETSI GS NFV-SOL 002 (Ve-Vnfm reference point, between a VNF and its VNF manager) and ETSI GS NFV-SOL 003 (Or-Vnfm reference point, between an NFV orchestrator and a VNF manager). Covers VNF lifecycle management, lifecycle operation granting, LCM coordination, fault management, performance management, indicators, configuration, VNF package management, snapshot packages and their notification interfaces.

- **Human URL:** [https://forge.etsi.org/rep/nfv/SOL002-SOL003](https://forge.etsi.org/rep/nfv/SOL002-SOL003)

#### Tags

- NFV
- Orchestration
- Lifecycle Management
- Virtualisation

#### Properties

- [Documentation](https://www.etsi.org/technologies/nfv)
- [APIReference](https://forge.etsi.org/rep/nfv/SOL002-SOL003)
- [Repository](https://forge.etsi.org/rep/nfv/SOL002-SOL003)
- **25 OpenAPI documents** — see `apis.yml` for the full list; first: [openapi/nfv-sol002-sol003/SOL002/APIVersion/APIVersion.yaml](openapi/nfv-sol002-sol003/SOL002/APIVersion/APIVersion.yaml)

### ETSI NFV SOL005 Os-Ma-nfvo Network Service Management APIs

The RESTful protocols and data models of ETSI GS NFV-SOL 005 on the Os-Ma-nfvo reference point, between an OSS/BSS and an NFV orchestrator. Covers network service descriptor management, network service lifecycle management, NS fault and performance management, NFVI capacity information, VNF package management and VNF snapshot package management.

- **Human URL:** [https://forge.etsi.org/rep/nfv/SOL005](https://forge.etsi.org/rep/nfv/SOL005)

#### Tags

- NFV
- Orchestration
- Network Service
- OSS

#### Properties

- [Documentation](https://www.etsi.org/technologies/nfv)
- [APIReference](https://forge.etsi.org/rep/nfv/SOL005)
- [Repository](https://forge.etsi.org/rep/nfv/SOL005)
- **15 OpenAPI documents** — see `apis.yml` for the full list; first: [openapi/nfv-sol005/SOL005/APIVersion/APIVersion.yaml](openapi/nfv-sol005/SOL005/APIVersion/APIVersion.yaml)

### ETSI NFV SOL009 NFV-MANO Management APIs

The RESTful protocols and data models of ETSI GS NFV-SOL 009 for managing the NFV management-and-orchestration functions themselves, covering NFV-MANO configuration and information management, fault management, performance management and log management together with their notification interfaces.

- **Human URL:** [https://forge.etsi.org/rep/nfv/SOL009](https://forge.etsi.org/rep/nfv/SOL009)

#### Tags

- NFV
- MANO
- Management
- Observability

#### Properties

- [Documentation](https://www.etsi.org/technologies/nfv)
- [APIReference](https://forge.etsi.org/rep/nfv/SOL009)
- [Repository](https://forge.etsi.org/rep/nfv/SOL009)
- **9 OpenAPI documents** — see `apis.yml` for the full list; first: [openapi/nfv-sol009/SOL009/APIVersion/APIVersion.yaml](openapi/nfv-sol009/SOL009/APIVersion/APIVersion.yaml)

### ETSI NFV SOL011 Or-Or Multi-Administrative-Domain APIs

The RESTful protocols and data models of ETSI GS NFV-SOL 011 on the Or-Or reference point, used between NFV orchestrators in different administrative domains for nested network service descriptor management, lifecycle management, granting, usage notification, fault and performance management.

- **Human URL:** [https://forge.etsi.org/rep/nfv/SOL011](https://forge.etsi.org/rep/nfv/SOL011)

#### Tags

- NFV
- Orchestration
- Federation
- Multi-Domain

#### Properties

- [Documentation](https://www.etsi.org/technologies/nfv)
- [APIReference](https://forge.etsi.org/rep/nfv/SOL011)
- [Repository](https://forge.etsi.org/rep/nfv/SOL011)
- **10 OpenAPI documents** — see `apis.yml` for the full list; first: [openapi/nfv-sol011/SOL011/APIVersion/APIVersion.yaml](openapi/nfv-sol011/SOL011/APIVersion/APIVersion.yaml)

### ETSI NFV SOL012 Policy Management API

The RESTful protocol and data model of ETSI GS NFV-SOL 012 for policy management across NFV management and orchestration, covering policy transfer, activation, deactivation, deletion and the associated policy notification interface.

- **Human URL:** [https://forge.etsi.org/rep/nfv/SOL012](https://forge.etsi.org/rep/nfv/SOL012)

#### Tags

- NFV
- Policy
- Governance

#### Properties

- [Documentation](https://www.etsi.org/technologies/nfv)
- [APIReference](https://forge.etsi.org/rep/nfv/SOL012)
- [Repository](https://forge.etsi.org/rep/nfv/SOL012)
- [OpenAPI](openapi/nfv-sol012/SOL012/APIVersion/APIVersion.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [OpenAPI](openapi/nfv-sol012/SOL012/PolicyManagement/PolicyManagement.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [OpenAPI](openapi/nfv-sol012/SOL012/PolicyManagementNotification/PolicyManagementNotification.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI NGSI-LD API (ISG CIM)

The NGSI-LD API standardised by ETSI ISG CIM in GS CIM 009, a JSON-LD context information management API for entities, attributes, relationships, subscriptions, temporal queries, entity types, context source registration and distributed federation. It is the API layer beneath most European smart-city and FIWARE deployments and is published as OpenAPI 3.0.3 and 3.1.0.

- **Human URL:** [https://forge.etsi.org/rep/cim/ngsi-ld-openapi](https://forge.etsi.org/rep/cim/ngsi-ld-openapi)

#### Tags

- Context Information
- NGSI-LD
- Smart Cities
- IoT
- JSON-LD

#### Properties

- [Documentation](https://www.etsi.org/technologies/context-information-management)
- [APIReference](https://forge.etsi.org/rep/cim/ngsi-ld-openapi)
- [Repository](https://forge.etsi.org/rep/cim/ngsi-ld-openapi)
- [OpenAPI](openapi/ngsi-ld/ngsi-ld-api-3.0.3.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [OpenAPI](openapi/ngsi-ld/ngsi-ld-api-3.1.0.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI OpenCAPIF (3GPP CAPIF TS 29.222) APIs

The ETSI Software Development Group implementation of the 3GPP Common API Framework, TS 29.222. Harvested here are the API Invoker Management, API Provider Management, Access Control Policy and Auditing service APIs — the northbound framework a mobile operator uses to onboard API invokers, register API providers, enforce per-invoker access policy and audit invocation logs. Authorisation is OAuth 2.0 client credentials.

- **Human URL:** [https://ocf.etsi.org/documentation/latest/](https://ocf.etsi.org/documentation/latest/)

#### Tags

- 3GPP
- CAPIF
- API Management
- Network Exposure
- 5G

#### Properties

- [Documentation](https://ocf.etsi.org/documentation/latest/)
- [APIReference](https://ocf.etsi.org/documentation/latest/)
- [Repository](https://labs.etsi.org/rep/ocf/capif)
- [OpenAPI](openapi/capif/capif-access-control-policy.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [OpenAPI](openapi/capif/capif-api-invoker-management.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [OpenAPI](openapi/capif/capif-api-provider-management.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [OpenAPI](openapi/capif/capif-auditing.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI OpenSlice CAMARA-as-a-Service QoD Provisioning API

A CAMARA Quality on Demand (QoD) Provisioning API implementation shipped as an add-on to ETSI OpenSlice. It wraps a running TM Forum service inventory entry so an operator can expose an existing 5G core or network slice through a standard CAMARA endpoint: set, retrieve and delete a device QoS profile. Security is declared as OpenID Connect, matching the CAMARA authorisation model; no CIBA grant is declared in this document.

- **Human URL:** [https://labs.etsi.org/rep/osl/code/addons/org.etsi.osl.controllers.camara](https://labs.etsi.org/rep/osl/code/addons/org.etsi.osl.controllers.camara)

#### Tags

- CAMARA
- Quality on Demand
- Network APIs
- 5G
- Network Slicing

#### Properties

- [Documentation](https://osl.etsi.org/documentation/latest/)
- [APIReference](https://labs.etsi.org/rep/osl/code/addons/org.etsi.osl.controllers.camara)
- [Repository](https://labs.etsi.org/rep/osl/code/addons/org.etsi.osl.controllers.camara)
- [OpenAPI](openapi/camara/openslice-camara-qod-provisioning.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI Operator Platform Open Exposure Gateway API

The Open Exposure Gateway of the ETSI Operator Platform SDG, implementing the Open Exposure Gateway role defined by the GSMA Operator Platform Group. It exposes northbound CAMARA APIs to application providers: Edge Cloud Management (application metadata and instance lifecycle, edge cloud zones), Network Exposure (Quality on Demand sessions and device location retrieval) and Federation Management across partner operator platforms.

- **Human URL:** [https://labs.etsi.org/rep/oop/code/open-exposure-gateway](https://labs.etsi.org/rep/oop/code/open-exposure-gateway)

#### Tags

- CAMARA
- GSMA
- Operator Platform
- Edge Computing
- Federation
- Quality on Demand

#### Properties

- [Documentation](https://labs.etsi.org/rep/oop/code/open-exposure-gateway)
- [APIReference](https://labs.etsi.org/rep/oop/code/open-exposure-gateway)
- [Repository](https://labs.etsi.org/rep/oop/code/open-exposure-gateway)
- [OpenAPI](openapi/camara/operator-platform-edge-cloud-management.yaml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ETSI OpenSlice TM Forum Open APIs

ETSI SDG OpenSlice is an open-source service-based OSS delivering Network as a Service, and it exposes its catalog, ordering and inventory surface as TM Forum Open APIs. The documentation lists more than twenty exposed endpoints including TMF620 Product Catalog, TMF622 Product Ordering, TMF629 Customer, TMF632 Party, TMF633 Service Catalog, TMF634 Resource Catalog, TMF638 Service Inventory, TMF639 Resource Inventory, TMF640 Service Activation, TMF641 Service Ordering, TMF642 Alarm, TMF651 Agreement, TMF652 Resource Ordering, TMF653 Service Test, TMF657 Service Quality, TMF666 Account, TMF669 Party Role, TMF685 Resource Pool and TMF691 Federated ID. The public OpenSlice demo answers these paths anonymously; ETSI does not hold a TM Forum Open API conformance certification for them.

- **Human URL:** [https://osl.etsi.org/documentation/latest/naas/exposed_apis/](https://osl.etsi.org/documentation/latest/naas/exposed_apis/)
- **Base URL:** `https://portal.openslice.eu/tmf-api`

#### Tags

- TM Forum
- Open APIs
- OSS
- BSS
- Service Ordering
- Network as a Service

#### Properties

- [Documentation](https://osl.etsi.org/documentation/latest/naas/exposed_apis/)
- [APIReference](https://osl.etsi.org/documentation/latest/naas/exposed_apis/)
- [Repository](https://labs.etsi.org/rep/osl/code/org.etsi.osl.tmf.api)
- [Demo](https://portal.openslice.eu/)
- [Website](https://osl.etsi.org/)

### ETSI MEC Sandbox / EdgeNative Connector

A hosted, free interactive environment where developers exercise live ETSI MEC service APIs against emulated 4G, 5G and Wi-Fi network scenarios with moving user equipment. It serves MEC 011, MEC 012, MEC 013, MEC 021, MEC 028, MEC 030 and MEC 040 through a Swagger UI try-it console, and version 1.10 added alignment with 3GPP CAPIF and initial 3GPP EDGEAPP support. The web front end loads anonymously but the API paths themselves return HTTP 401 until you sign in, so it is free-but-account-gated rather than open.

- **Human URL:** [https://try-mec.etsi.org/](https://try-mec.etsi.org/)
- **Base URL:** `https://try-mec.etsi.org`

#### Tags

- Edge Computing
- MEC
- Sandbox
- Developer Experience
- 5G

#### Properties

- [Documentation](https://mecwiki.etsi.org/index.php?title=MEC_Sandbox_Help)
- [APIReference](https://mecwiki.etsi.org/index.php?title=MEC_Sandbox_Help)
- [Repository](https://labs.etsi.org/rep/mec/etsi-mec-sandbox)

## Common Properties

- [Website](https://www.etsi.org/)
- [Documentation](https://www.etsi.org/standards/get-standards)
- [Standards](https://www.etsi.org/deliver/)
- [Portal](https://portal.etsi.org/)
- [Repository](https://forge.etsi.org/rep/)
- [Repository](https://labs.etsi.org/rep/)
- [License](https://forge.etsi.org/legal-matters)
- [Sandbox](https://try-mec.etsi.org/)
- [Wiki](https://mecwiki.etsi.org/)
- [OpenSource](https://osl.etsi.org/)
- [OpenSource](https://ocf.etsi.org/)
- [OpenSource](https://tfs.etsi.org/)
- [OpenSource](https://osm.etsi.org/)
- [BlogRSS](https://www.etsi.org/feed)
- [LinkedIn](https://www.linkedin.com/company/etsi)
- [GitHubOrganization](https://github.com/etsi-forge)

## Maintainers

- Kin Lane — kin@apievangelist.com
