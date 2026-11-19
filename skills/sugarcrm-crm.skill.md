---
name: sugarcrm-crm
description: 'Manage SugarCRM contacts, accounts, and opportunities. Use when the
  user mentions sugarcrm, sugar, CRM, contact, account, opportunity, lead.

  '
version: 1.0.0
skill_type: external
base_url_env: SUGARCRM_BASE_URL
auth_env_var: SUGARCRM_ACCESS_TOKEN
auth_type: bearer
triggers:
  - sugarcrm
  - sugar
  - CRM
  - contact
  - account
  - opportunity
  - lead
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SUGARCRM_BASE_URL and SUGARCRM_ACCESS_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Sugarcrm-Crm

Manage SugarCRM contacts, accounts, and opportunities. Use when the user mentions sugarcrm, sugar, CRM, contact, account, opportunity, lead.


## API Endpoints

- **GET** `/rest/v11_5/{module}` - List records
- **GET** `/rest/v11_5/{module}/{record_id}` - Get a record
- **POST** `/rest/v11_5/{module}` - Create a record
- **PUT** `/rest/v11_5/{module}/{record_id}` - Update a record
- **DELETE** `/rest/v11_5/{module}/{record_id}` - Delete a record
- **POST** `/rest/v11_5/{module}/filter` - Filter records
- **GET** `/rest/v11_5/me` - Get current user
- **GET** `/rest/v11_5/metadata` - Get metadata

## Actions

- get_by_id: List records (GET /rest/v11_5/{module})
- get_record: Get a record (GET /rest/v11_5/{module}/{record_id})
- add: Create a record (POST /rest/v11_5/{module})
- update: Update a record (PUT /rest/v11_5/{module}/{record_id})
- delete: Delete a record (DELETE /rest/v11_5/{module}/{record_id})
- create: Filter records (POST /rest/v11_5/{module}/filter)
- list: Get current user (GET /rest/v11_5/me)
- get_metadata: Get metadata (GET /rest/v11_5/metadata)

## Fields

- `name`: string [REQUIRED for create accounts] — Display name
- `first_name`: string [REQUIRED for create contacts] — First display name
- `last_name`: string [REQUIRED for create contacts] — Last display name
- `email`: string [OPTIONAL] — Email address
- `phone_work`: string [OPTIONAL] — Phone Work
- `description`: string [OPTIONAL] — Human-readable description
- `assigned_user_id`: string [OPTIONAL] — Assigned User unique identifier

## Example Request Bodies

**Create Contact:**
```json
{"first_name": "John", "last_name": "Doe", "email": "john@example.com", "phone_work": "+15551234567"}
```

**Create Account:**
```json
{"name": "Acme Corporation", "description": "Enterprise client"}
```

## Response

**Rest object:**
- `id`: string — Unique rest identifier
- `name`: string — Rest name or title
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
