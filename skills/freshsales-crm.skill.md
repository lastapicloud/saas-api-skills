---
name: freshsales-crm
description: 'Manage contacts, accounts, and deals in Freshsales CRM. Use when the
  user mentions freshsales, freshworks crm, freshsales contact, freshsales deal, freshsales
  account.

  '
version: 1.0.0
skill_type: external
base_url_env: FRESHSALES_BASE_URL
auth_env_var: FRESHSALES_API_KEY
auth_type: header
triggers:
  - freshsales
  - freshworks crm
  - freshsales contact
  - freshsales deal
  - freshsales account
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FRESHSALES_BASE_URL and FRESHSALES_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Freshsales-Crm

Manage contacts, accounts, and deals in Freshsales CRM. Use when the user mentions freshsales, freshworks crm, freshsales contact, freshsales deal, freshsales account.


## API Endpoints

- **GET** `/crm/sales/api/contacts/view/{view_id}` - List contacts by view
- **POST** `/crm/sales/api/contacts` - Create a contact
- **GET** `/crm/sales/api/contacts/{id}` - Get a contact by ID
- **PUT** `/crm/sales/api/contacts/{id}` - Update a contact
- **DELETE** `/crm/sales/api/contacts/{id}` - Delete a contact
- **GET** `/crm/sales/api/deals/view/{view_id}` - List deals by view
- **POST** `/crm/sales/api/deals` - Create a deal
- **GET** `/crm/sales/api/sales_accounts` - List accounts
- **POST** `/crm/sales/api/sales_accounts` - Create an account
- **POST** `/api/contacts`
- **GET** `/api/contacts/` - Use 'include' to embed additional details in the response.
- **GET** `/api/contacts/view/` - You can filter your contacts and also sort them to get a list of specific contacts
- **GET** `/api/contacts/filters`
- **PUT** `/api/contacts/`
- **POST** `/api/contacts/`

## Actions

- get_by_id: List contacts by view (GET /crm/sales/api/contacts/view/{view_id})
- create: Create a contact (POST /crm/sales/api/contacts)
- get_contact_id: Get a contact by ID (GET /crm/sales/api/contacts/{id})
- update: Update a contact (PUT /crm/sales/api/contacts/{id})
- delete: Delete a contact (DELETE /crm/sales/api/contacts/{id})
- list_deals_view: List deals by view (GET /crm/sales/api/deals/view/{view_id})
- create_deal: Create a deal (POST /crm/sales/api/deals)
- list: List accounts (GET /crm/sales/api/sales_accounts)
- create_account: Create an account (POST /crm/sales/api/sales_accounts)
- create_contacts: POST /api/contacts (POST /api/contacts)
- get_use_include_embed_additional: Use 'include' to embed additional details in the response. (GET /api/contacts/)
- get_you_can_filter_your: You can filter your contacts and also sort them to get a list of specific contac (GET /api/contacts/view/)
- list_filters: GET /api/contacts/filters (GET /api/contacts/filters)
- put_contacts: PUT /api/contacts/ (PUT /api/contacts/)
- post_api_contacts: POST /api/contacts/ (POST /api/contacts/)

## Fields

- `id`: integer [REQUIRED for get_contact, update_contact, delete_contact] (record ID) — Unique identifier
- `view_id`: integer [REQUIRED for list_contacts, list_deals] (view ID) — View unique identifier
- `first_name`: string [OPTIONAL] (first name) — First display name
- `last_name`: string [REQUIRED for create_contact] (last name) — Last display name
- `email`: string [OPTIONAL] (email address) — Email address
- `mobile_number`: string [OPTIONAL] (mobile phone) — Mobile Number
- `job_title`: string [OPTIONAL] (job title) — Job title or heading
- `name`: string [REQUIRED for create_deal, create_account] (deal or account name) — Display name
- `amount`: number [OPTIONAL] (deal amount) — Amount in smallest currency unit

## Example Request Bodies

**Create Contact:**
```json
{"contact": {"first_name": "Jane", "last_name": "Doe", "email": "jane@example.com", "job_title": "Manager"}}
```

**Create Deal:**
```json
{"deal": {"name": "Enterprise License", "amount": 50000}}
```

## Response

**Contact object:**
- `id`: string — Unique contact identifier
- `name`: string — Contact name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "id": 1,
  "view_id": 1
}
```


**Required fields reference:**
```json
{
  "id": 1,
  "view_id": 1
}
```

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
