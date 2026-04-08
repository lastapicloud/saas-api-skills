---
name: wise-payments
description: Manage transfers and accounts via Wise. Use when the user mentions wise,
  transferwise, transfer, payment, currency, exchange.
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
