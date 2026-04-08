---
name: vtiger-crm
description: Manage Vtiger CRM contacts, deals, and organizations. Use when the user
  mentions vtiger, CRM, contact, deal, lead, organization.
version: 1.0.0
skill_type: external
base_url_env: VTIGER_BASE_URL
auth_env_var: VTIGER_ACCESS_KEY
auth_type: header
triggers:
  - vtiger
  - CRM
  - contact
  - deal
  - lead
  - organization
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires VTIGER_BASE_URL and VTIGER_ACCESS_KEY environment variables.
---

# Vtiger-Crm

Manage Vtiger CRM contacts, deals, and organizations. Use when the user mentions vtiger, CRM, contact, deal, lead, organization.

## API Endpoints

- **GET** `/restapi/v1/vtiger/default/query?query={query}` - Query records via VQL (list)
- **GET** `/restapi/v1/vtiger/default/retrieve?id={id}` - Get single record (get_by_id)
- **POST** `/restapi/v1/vtiger/default/create` - Create new record (create)
- **PUT** `/restapi/v1/vtiger/default/revise` - Full record update (update)
- **PUT** `/restapi/v1/vtiger/default/update` - Partial field update (update_fields)
- **DELETE** `/restapi/v1/vtiger/default/delete` - Delete record (delete)
- **PUT** `/restapi/v1/vtiger/default/undelete` - Restore deleted record (restore)
- **PUT** `/restapi/v1/vtiger/default/sync` - Sync modified records (sync)
- **PUT** `/restapi/v1/vtiger/default/convert` - Convert lead to contact/deal (convert)
- **PUT** `/restapi/v1/vtiger/default/massadd` - Bulk create records (bulk_create)
- **GET** `/restapi/v1/vtiger/default/describe?elementType={module}` - Describe module (describe)
- **GET** `/restapi/v1/vtiger/default/listtypes` - List available modules (list_types)
- **GET** `/restapi/v1/vtiger/default/me` - Get current user

## Actions

- query: Query records via VQL (list) (GET /restapi/v1/vtiger/default/query?query={query})
- list: Get single record (get_by_id) (GET /restapi/v1/vtiger/default/retrieve?id={id})
- create: Create new record (create) (POST /restapi/v1/vtiger/default/create)
- put_revise: Full record update (update) (PUT /restapi/v1/vtiger/default/revise)
- put_update: Partial field update (update_fields) (PUT /restapi/v1/vtiger/default/update)
- delete_delete: Delete record (delete) (DELETE /restapi/v1/vtiger/default/delete)
- put_undelete: Restore deleted record (restore) (PUT /restapi/v1/vtiger/default/undelete)
- put_sync: Sync modified records (sync) (PUT /restapi/v1/vtiger/default/sync)
- put_convert: Convert lead to contact/deal (convert) (PUT /restapi/v1/vtiger/default/convert)
- put_massadd: Bulk create records (bulk_create) (PUT /restapi/v1/vtiger/default/massadd)
- list_describeelementtypemodule: Describe module (describe) (GET /restapi/v1/vtiger/default/describe?elementType={module})
- list_listtypes: List available modules (list_types) (GET /restapi/v1/vtiger/default/listtypes)
- list_me: Get current user (GET /restapi/v1/vtiger/default/me)

## Fields

- `elementType`: string [REQUIRED for create] (e.g., "Contacts", "Potentials", "Organizations")
- `element`: JSON string [REQUIRED for create] with module-specific fields
- `id`: string [REQUIRED for update/delete]
- `query`: string [REQUIRED for query] (VQL query string)

## Example Request Bodies

**Create Record:**
```json
{"elementType": "Contacts", "element": "{\"firstname\": \"John\", \"lastname\": \"Doe\", \"email\": \"john@example.com\"}"}
```

**Update Record:**
```json
{"id": "12x345", "element": "{\"email\": \"john.doe@newdomain.com\"}"}
```
