---
name: nutshell-crm
description: 'Manage contacts, leads, and accounts in Nutshell CRM. Use when the user
  mentions nutshell, nutshell crm, nutshell lead, nutshell contact, nutshell account.

  '
version: 1.0.0
skill_type: external
base_url_env: NUTSHELL_BASE_URL
auth_env_var: NUTSHELL_API_KEY
auth_type: basic
triggers:
  - nutshell
  - nutshell crm
  - nutshell lead
  - nutshell contact
  - nutshell account
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires NUTSHELL_BASE_URL and NUTSHELL_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Nutshell-Crm

Manage contacts, leads, and accounts in Nutshell CRM. Use when the user mentions nutshell, nutshell crm, nutshell lead, nutshell contact, nutshell account.


## API Endpoints

- **GET** `/api/v1/contacts` - List contacts
- **POST** `/api/v1/contacts` - Create a contact
- **GET** `/api/v1/contacts/{id}` - Get a contact by ID
- **PUT** `/api/v1/contacts/{id}` - Update a contact
- **DELETE** `/api/v1/contacts/{id}` - Delete a contact
- **GET** `/api/v1/leads` - List leads
- **POST** `/api/v1/leads` - Create a lead
- **GET** `/api/v1/leads/{id}` - Get a lead by ID
- **GET** `/api/v1/accounts` - List accounts
- **POST** `/api/v1/accounts` - Create an account

## Actions

- list: List contacts (GET /api/v1/contacts)
- create: Create a contact (POST /api/v1/contacts)
- get_by_id: Get a contact by ID (GET /api/v1/contacts/{id})
- update: Update a contact (PUT /api/v1/contacts/{id})
- delete: Delete a contact (DELETE /api/v1/contacts/{id})
- list_leads: List leads (GET /api/v1/leads)
- create_lead: Create a lead (POST /api/v1/leads)
- get_lead_id: Get a lead by ID (GET /api/v1/leads/{id})
- list_accounts: List accounts (GET /api/v1/accounts)
- create_account: Create an account (POST /api/v1/accounts)

## Fields

- `id`: integer [REQUIRED for get_contact, update_contact, delete_contact, get_lead] (record ID) — Unique identifier
- `name`: string [REQUIRED for create_contact, create_account] (name) — Display name
- `email`: string [OPTIONAL] (email address) — Email address
- `phone`: string [OPTIONAL] (phone number) — Phone number
- `description`: string [OPTIONAL] (lead or account description) — Human-readable description
- `value`: number [OPTIONAL] (lead value) — Value
- `confidence`: integer [OPTIONAL] (lead confidence percentage) — Confidence value

## Example Request Bodies

**Create Contact:**
```json
{"name": "Jane Doe", "email": "jane@example.com", "phone": "+1234567890"}
```

**Create Lead:**
```json
{"name": "Enterprise Deal", "value": 50000, "confidence": 75}
```

## Response

**Contact object:**
- `id`: string — Unique contact identifier
- `name`: string — Contact name or title
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
