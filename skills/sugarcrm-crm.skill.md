---
name: sugarcrm-crm
description: Manage SugarCRM contacts, accounts, and opportunities. Use when the user
  mentions sugarcrm, sugar, CRM, contact, account, opportunity, lead.
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
- get_by_id_v11_5: Get a record (GET /rest/v11_5/{module}/{record_id})
- add_v11_5: Create a record (POST /rest/v11_5/{module})
- update: Update a record (PUT /rest/v11_5/{module}/{record_id})
- delete: Delete a record (DELETE /rest/v11_5/{module}/{record_id})
- create: Filter records (POST /rest/v11_5/{module}/filter)
- list: Get current user (GET /rest/v11_5/me)
- list_metadata: Get metadata (GET /rest/v11_5/metadata)

## Fields

- `name`: string [REQUIRED for create accounts]
- `first_name`: string [REQUIRED for create contacts]
- `last_name`: string [REQUIRED for create contacts]
- `email`: string [OPTIONAL]
- `phone_work`: string [OPTIONAL]
- `description`: string [OPTIONAL]
- `assigned_user_id`: string [OPTIONAL]

## Example Request Bodies

**Create Contact:**
```json
{"first_name": "John", "last_name": "Doe", "email": "john@example.com", "phone_work": "+15551234567"}
```

**Create Account:**
```json
{"name": "Acme Corporation", "description": "Enterprise client"}
```
