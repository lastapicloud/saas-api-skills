---
name: dynamics365-crm
description: 'Manage accounts, contacts, and opportunities via Dynamics 365. Use when
  the user mentions dynamics 365, dynamics, crm, account, contact, opportunity, lead.

  '
version: 1.0.0
skill_type: external
base_url_env: DYNAMICS365_BASE_URL
auth_env_var: DYNAMICS365_ACCESS_TOKEN
auth_type: bearer
triggers:
  - dynamics 365
  - dynamics
  - crm
  - account
  - contact
  - opportunity
  - lead
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: 'Requires DYNAMICS365_BASE_URL and DYNAMICS365_ACCESS_TOKEN environment
  variables.

  '
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Dynamics365-Crm

Manage accounts, contacts, and opportunities via Dynamics 365. Use when the user mentions dynamics 365, dynamics, crm, account, contact, opportunity, lead.


## API Endpoints

- **GET** `/api/data/v9.2/accounts` - List accounts
- **POST** `/api/data/v9.2/accounts` - Create an account
- **GET** `/api/data/v9.2/accounts({accountid})` - Get account by ID
- **PATCH** `/api/data/v9.2/accounts({accountid})` - Update an account
- **DELETE** `/api/data/v9.2/accounts({accountid})` - Delete an account
- **GET** `/api/data/v9.2/contacts` - List contacts
- **GET** `/api/data/v9.2/opportunities` - List opportunities
- **GET** `/api/data/v9.2/leads` - List leads

## Actions

- list: List accounts (GET /api/data/v9.2/accounts)
- create: Create an account (POST /api/data/v9.2/accounts)
- get_account_id: Get account by ID (GET /api/data/v9.2/accounts({accountid}))
- patch_accounts({accountid}): Update an account (PATCH /api/data/v9.2/accounts({accountid}))
- delete_accounts({accountid}): Delete an account (DELETE /api/data/v9.2/accounts({accountid}))
- list_contacts: List contacts (GET /api/data/v9.2/contacts)
- list_opportunities: List opportunities (GET /api/data/v9.2/opportunities)
- list_leads: List leads (GET /api/data/v9.2/leads)

## Fields

- `name`: string [REQUIRED for create] — Display name
- `emailaddress1`: string [OPTIONAL] — Emailaddress1
- `telephone1`: string [OPTIONAL] — Telephone1

## Example Request Bodies

**Create Account:**
```json
{"name": "Contoso Ltd", "emailaddress1": "info@contoso.com", "telephone1": "+1-555-0100"}
```

**Update Account:**
```json
{"name": "Contoso Corporation", "emailaddress1": "contact@contoso.com"}

## Response

**Accounts({Accountid}) object:**
- `id`: string — Unique accounts({accountid}) identifier
- `name`: string — Accounts({Accountid}) name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 404 | Resource not found — check the ID or identifier |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
