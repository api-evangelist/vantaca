# Vantaca (vantaca)

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

Vantaca is a cloud-based community association and HOA management software platform for management companies, boards, and homeowners. It covers accounting and accounts payable, homeowner accounts and ledgers, action-item workflow automation (violations, architectural/ARC requests, work orders, collections), communications, and vendor/service-provider management.

Vantaca exposes a **real, documented public REST API** - "Vantaca's Standard APIs" (v3.8.0), a JSON web service. The OpenAPI 3.0 definition is published on SwaggerHub, so the full endpoint surface is discoverable. **Access is documented but gated:** it is not self-serve. Each Vantaca customer (a management company) authorizes a vendor to reach that customer's own dataset, and Vantaca provisions scoped credentials plus IP whitelisting. Vendors request access via `vendorsupport@vantaca.com`.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/vantaca/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/vantaca/refs/heads/main/apis.yml)

## Access Model

- **Production base URL:** `https://api.vantaca.net`
- **Format:** JSON over HTTPS/SSL (SSL required). Both GET and POST are accepted.
- **Authentication:** HTTP Basic authorization, plus three required parameters on **all** endpoints: `company`, `login`, `pwd`.
- **Authorization:** Credentials are granted per-customer - a Vantaca customer grants a vendor access to their dataset; credentials vary from one customer to another.
- **Network:** Each credential set must have one or more **whitelisted IP addresses**.
- **Requesting access:** Email `vendorsupport@vantaca.com` to have an API user created and IPs whitelisted.
- **Bulk reads:** Most `/read/` methods accept an optional `zip=true` parameter that returns a compressed `data.json`, recommended for company-wide pulls.
- **Pricing:** No public, self-serve API pricing. API access is a platform capability; management companies contact Vantaca sales.

The published OpenAPI (v3.8.0) defines **75 operations** across three groups: `/read/`, `/write/`, and `/AP/` (accounts payable). The logical APIs below are an API Evangelist curation of that single specification.

## Tags

- HOA
- Community Association Management
- CAM
- Property Management
- Real Estate
- Accounting
- Workflow Automation
- Vendor Management

## Timestamps

- **Created:** 2026-07-04
- **Modified:** 2026-07-04

## APIs

### Vantaca Associations API

Retrieve the associations (communities) a vendor has been granted access to, along with association details, additional info, and address records.

- **API Reference:** [https://app.swaggerhub.com/apis/Vantaca/vantacaStandard/3.8.0](https://app.swaggerhub.com/apis/Vantaca/vantacaStandard/3.8.0)
- **Base URL:** `https://api.vantaca.net`
- **OpenAPI:** [openapi/vantaca-openapi.json](openapi/vantaca-openapi.json)

### Vantaca Homeowner Accounts API

Look up homeowner accounts and their financial and contact records - account info, homeowner search, transactions, assessments, tenants, and CRUD on a homeowner's address, email, phone, name, and communication/billing preferences.

- **API Reference:** [https://app.swaggerhub.com/apis/Vantaca/vantacaStandard/3.8.0](https://app.swaggerhub.com/apis/Vantaca/vantacaStandard/3.8.0)
- **Base URL:** `https://api.vantaca.net`
- **OpenAPI:** [openapi/vantaca-openapi.json](openapi/vantaca-openapi.json)

### Vantaca Accounts Payable & Ledger API

Manage association accounting - create, read, update, pay, void, and delete invoices; list payments; retrieve GL codes, funds, bank accounts and balances, GL transaction history; and create, update, write off, or delete homeowner ledger entries.

- **API Reference:** [https://app.swaggerhub.com/apis/Vantaca/vantacaStandard/3.8.0](https://app.swaggerhub.com/apis/Vantaca/vantacaStandard/3.8.0)
- **Base URL:** `https://api.vantaca.net`
- **OpenAPI:** [openapi/vantaca-openapi.json](openapi/vantaca-openapi.json)

### Vantaca Work Orders API

List and create work-order action items against an association, part of Vantaca's action-item workflow engine.

- **API Reference:** [https://app.swaggerhub.com/apis/Vantaca/vantacaStandard/3.8.0](https://app.swaggerhub.com/apis/Vantaca/vantacaStandard/3.8.0)
- **Base URL:** `https://api.vantaca.net`
- **OpenAPI:** [openapi/vantaca-openapi.json](openapi/vantaca-openapi.json)

### Vantaca Violations & Compliance API

Retrieve violations and the CC&R rule items and violation types they reference, and create new violation action items.

- **API Reference:** [https://app.swaggerhub.com/apis/Vantaca/vantacaStandard/3.8.0](https://app.swaggerhub.com/apis/Vantaca/vantacaStandard/3.8.0)
- **Base URL:** `https://api.vantaca.net`
- **OpenAPI:** [openapi/vantaca-openapi.json](openapi/vantaca-openapi.json)

### Vantaca Architectural Requests (ARC) API

List and create Architectural Review Committee (ARC) request action items for homeowner modification requests.

- **API Reference:** [https://app.swaggerhub.com/apis/Vantaca/vantacaStandard/3.8.0](https://app.swaggerhub.com/apis/Vantaca/vantacaStandard/3.8.0)
- **Base URL:** `https://api.vantaca.net`
- **OpenAPI:** [openapi/vantaca-openapi.json](openapi/vantaca-openapi.json)

### Vantaca Vendors & Service Providers API

Manage service providers (vendors) and their insurance records - list providers and provider types, read a single provider, create and update providers, and CRUD provider insurance.

- **API Reference:** [https://app.swaggerhub.com/apis/Vantaca/vantacaStandard/3.8.0](https://app.swaggerhub.com/apis/Vantaca/vantacaStandard/3.8.0)
- **Base URL:** `https://api.vantaca.net`
- **OpenAPI:** [openapi/vantaca-openapi.json](openapi/vantaca-openapi.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/vantaca)
- [Website](https://www.vantaca.com)
- [Documentation](https://app.swaggerhub.com/apis/Vantaca/vantacaStandard/3.8.0)
- [Plans](plans/vantaca-plans-pricing.yml)
- [Rate Limits](rate-limits/vantaca-rate-limits.yml)
- [Fin Ops](finops/vantaca-finops.yml)

## Review

Does Vantaca expose a documented public WebSocket API? **No.** Vantaca's own public API is request/response REST (Vantaca's Standard APIs v3.8.0 over HTTPS with Basic auth). No WebSocket (`ws://`/`wss://`) endpoint is documented, and no AsyncAPI document was authored. See [review.yml](review.yml).

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
