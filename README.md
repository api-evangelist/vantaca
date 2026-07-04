# Vantaca (vantaca)

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
