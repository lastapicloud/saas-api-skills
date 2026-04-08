---
name: nocodb-database
description: Manage bases, tables, and records via NocoDB. Use when the user mentions
  nocodb, database, table, record, no-code, airtable alternative.
version: 1.0.0
skill_type: external
base_url_env: NOCODB_BASE_URL
auth_env_var: NOCODB_API_TOKEN
auth_type: header
triggers:
  - nocodb
  - database
  - table
  - record
  - no-code
  - airtable alternative
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires NOCODB_BASE_URL and NOCODB_API_TOKEN environment variables.
---

# Nocodb-Database

Manage bases, tables, and records via NocoDB. Use when the user mentions nocodb, database, table, record, no-code, airtable alternative.

## API Endpoints

- **GET** `/api/v2/meta/bases` - List bases
- **GET** `/api/v2/meta/bases/{baseId}/tables` - List tables
- **GET** `/api/v2/tables/{tableId}/records` - List records
- **POST** `/api/v2/tables/{tableId}/records` - Create record
- **GET** `/api/v2/tables/{tableId}/records/{recordId}` - Get record
- **PATCH** `/api/v2/tables/{tableId}/records` - Update records
- **DELETE** `/api/v2/tables/{tableId}/records` - Delete records

## Actions

- list: List bases (GET /api/v2/meta/bases)
- list_tables: List tables (GET /api/v2/meta/bases/{baseId}/tables)
- list_records: List records (GET /api/v2/tables/{tableId}/records)
- create: Create record (POST /api/v2/tables/{tableId}/records)
- get_by_id: Get record (GET /api/v2/tables/{tableId}/records/{recordId})
- patch_records: Update records (PATCH /api/v2/tables/{tableId}/records)
- delete_records: Delete records (DELETE /api/v2/tables/{tableId}/records)

## Fields

- `tableId`: string [REQUIRED]
- `fields`: object [OPTIONAL for create]

## Example Request Bodies

**Create a Record:**
```json
{
  "fields": {
    "Title": "New Task",
    "Status": "In Progress",
    "Priority": "High"
  }
}
```

**Update Records:**
```json
{
  "records": [
    {
      "Id": 1,
      "fields": {
        "Status": "Completed"
      }
    }
  ]
}
```
