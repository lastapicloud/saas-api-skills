---
name: wise-payments
description: "Manage transfers and accounts via Wise. Use when the user mentions wise, transferwise, transfer, payment, currency, exchange."
version: 1.0.0
skill_type: external
base_url_env: WISE_BASE_URL
auth_env_var: WISE_API_TOKEN
auth_type: bearer
triggers:
  - wise
  - transferwise
  - transfer
  - payment
  - currency
  - exchange
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires WISE_BASE_URL and WISE_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Wise-Payments

Manage transfers and accounts via Wise. Use when the user mentions wise, transferwise, transfer, payment, currency, exchange.


## API Endpoints

- **GET** `/v1/profiles` - List profiles
- **POST** `/v1/quotes` - Create quote
- **GET** `/v1/quotes/{quoteId}` - Get quote
- **POST** `/v1/accounts` - Create recipient
- **GET** `/v1/accounts` - List recipients
- **POST** `/v1/transfers` - Create transfer
- **GET** `/v1/transfers/{transferId}` - Get transfer
- **GET** `/v1/borderless-accounts/{profileId}/balances` - Get balances
- **GET** `/v2/incidents` - Paginated incidents matching parameters
- **GET** `/v2/locations` - Unpaginated geojson response
- **GET** `/v2/locations/markers` - Unpaginated geojson response with simplestyled markers
- **GET** `/v2/incidents/{id}`
- **GET** `/access-policies` - Retrieves a paginated list of access policies for an identity (an IAM Identity Center user, an IAM Identity Center
- **POST** `/access-policies` - Creates an access policy that grants the specified identity (IAM Identity Center user, IAM Identity Center group, or
- **PUT** `/access-policies/{accessPolicyId}` - Updates an existing access policy that specifies an identity's access to an IoT SiteWise Monitor portal or project

## Actions

- list: List profiles (GET /v1/profiles)
- create: Create quote (POST /v1/quotes)
- get_by_id: Get quote (GET /v1/quotes/{quoteId})
- create_accounts: Create recipient (POST /v1/accounts)
- list_accounts: List recipients (GET /v1/accounts)
- create_transfers: Create transfer (POST /v1/transfers)
- get_by_id_transfers: Get transfer (GET /v1/transfers/{transferId})
- list_balances: Get balances (GET /v1/borderless-accounts/{profileId}/balances)
- list_incidents: Paginated incidents matching parameters (GET /v2/incidents)
- list_locations: Unpaginated geojson response (GET /v2/locations)
- list_markers: Unpaginated geojson response with simplestyled markers (GET /v2/locations/markers)
- get_by_id_incidents: GET /v2/incidents/{id} (GET /v2/incidents/{id})
- list_access_policies: Retrieves a paginated list of access policies for an identity (an IAM Identity C (GET /access-policies)
- create_access_policy: Creates an access policy that grants the specified identity (IAM Identity Center (POST /access-policies)
- update_access_policy: Updates an existing access policy that specifies an identity's access to an IoT (PUT /access-policies/{accessPolicyId})

## Fields

- `sourceCurrency`: string [REQUIRED for create_quote]
- `targetCurrency`: string [REQUIRED for create_quote]
- `sourceAmount`: number [REQUIRED for create_quote]
- `targetAccount`: integer [REQUIRED for create]
- `quoteUuid`: string [REQUIRED for create]

## Example Request Bodies

**Create Quote:**
```json
{"sourceCurrency": "USD", "targetCurrency": "EUR", "sourceAmount": 1000.00}
```

**Create Transfer:**
```json
{"targetAccount": 12345678, "quoteUuid": "a1b2c3d4-5678-90ab-cdef-1234567890ab"}

## Response

**list_access_policies response:**
- `accessPolicySummaries`: string
- `nextToken`: string

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request — missing required field, wrong type, or constraint violation |
| 401 | Authentication failed — check API credentials |
| 403 | Forbidden — insufficient permissions |
| 404 | Resource not found |
| 429 | Rate limited — retry after delay |
| 500 | Server error |
