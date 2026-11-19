---
name: activecampaign-crm
description: 'Manage contacts, deals, and automations in ActiveCampaign. Use when
  the user mentions activecampaign, active campaign, activecampaign contact, activecampaign
  deal, activecampaign automation.

  '
version: 1.0.0
skill_type: external
base_url_env: ACTIVECAMPAIGN_BASE_URL
auth_env_var: ACTIVECAMPAIGN_API_KEY
auth_type: header
triggers:
  - activecampaign
  - active campaign
  - activecampaign contact
  - activecampaign deal
  - activecampaign automation
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: 'Requires ACTIVECAMPAIGN_BASE_URL and ACTIVECAMPAIGN_API_KEY environment
  variables.

  '
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Activecampaign-Crm

Manage contacts, deals, and automations in ActiveCampaign. Use when the user mentions activecampaign, active campaign, activecampaign contact, activecampaign deal, activecampaign automation.


## API Endpoints

- **GET** `/api/3/contacts` - List contacts
- **POST** `/api/3/contacts` - Create a contact
- **GET** `/api/3/contacts/{id}` - Get a contact by ID
- **PUT** `/api/3/contacts/{id}` - Update a contact
- **DELETE** `/api/3/contacts/{id}` - Delete a contact
- **GET** `/api/3/deals` - List deals
- **POST** `/api/3/deals` - Create a deal
- **GET** `/api/3/dealStages` - List deal stages
- **GET** `/api/3/dealPipelines` - List deal pipelines
- **GET** `/api/3/automations` - List automations
- **POST** `/email`
- **POST** `/email/batch`

## Actions

- list: List contacts (GET /api/3/contacts)
- create: Create a contact (POST /api/3/contacts)
- get_by_id: Get a contact by ID (GET /api/3/contacts/{id})
- update: Update a contact (PUT /api/3/contacts/{id})
- delete: Delete a contact (DELETE /api/3/contacts/{id})
- list_deals: List deals (GET /api/3/deals)
- create_deal: Create a deal (POST /api/3/deals)
- list_deal_stages: List deal stages (GET /api/3/dealStages)
- list_deal_pipelines: List deal pipelines (GET /api/3/dealPipelines)
- list_automations: List automations (GET /api/3/automations)
- create_email: POST /email (POST /email)
- create_batch: POST /email/batch (POST /email/batch)

## Fields

- `id`: integer [REQUIRED for get_contact, update_contact, delete_contact] (record ID) — Unique identifier
- `email`: string [REQUIRED for create_contact] (contact email) — Email address
- `firstName`: string [OPTIONAL] (first name) — First display name
- `lastName`: string [OPTIONAL] (last name) — Last display name
- `phone`: string [OPTIONAL] (phone number) — Phone number
- `title`: string [REQUIRED for create_deal] (deal title) — Title or heading
- `value`: integer [OPTIONAL] (deal value in cents) — Value value
- `currency`: string [OPTIONAL] (deal currency code, e.g. usd) — Currency code (e.g., usd, eur)
- `group`: string [OPTIONAL] (pipeline ID) — Group
- `stage`: string [OPTIONAL] (stage ID) — Stage

## Example Request Bodies

**Create Contact:**
```json
{"contact": {"email": "jane@example.com", "firstName": "Jane", "lastName": "Doe", "phone": "+1234567890"}}
```

**Create Deal:**
```json
{"deal": {"title": "Enterprise License", "value": 5000000, "currency": "usd", "group": "1", "stage": "1"}}
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
