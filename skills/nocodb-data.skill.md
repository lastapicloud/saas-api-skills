---
name: nocodb-data
description: Manage NocoDB bases, tables, and records. Use when the user mentions
  nocodb, database, table, record, spreadsheet.
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
  - spreadsheet
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires NOCODB_BASE_URL and NOCODB_API_TOKEN environment variables.
---

# Nocodb-Data

Manage NocoDB bases, tables, and records. Use when the user mentions nocodb, database, table, record, spreadsheet.

## API Endpoints

- **GET** `/api/v2/meta/bases/` - List bases
- **GET** `/api/v2/meta/bases/{baseId}/tables` - List tables
- **GET** `/api/v2/public/shared-view/{sharedViewId}/rows` - List shared view rows
- **GET** `/api/v2/tables/{tableId}/records` - List records
- **GET** `/api/v2/tables/{tableId}/records/{recordId}` - Get a record
- **POST** `/api/v2/tables/{tableId}/records` - Create records
- **PATCH** `/api/v2/tables/{tableId}/records` - Update records
- **DELETE** `/api/v2/tables/{tableId}/records` - Delete records
- **GET** `/api/v2/meta/tables/{tableId}/columns` - List columns

## Actions

- list: List bases (GET /api/v2/meta/bases/)
- list_tables: List tables (GET /api/v2/meta/bases/{baseId}/tables)
- list_rows: List shared view rows (GET /api/v2/public/shared-view/{sharedViewId}/rows)
- list_records: List records (GET /api/v2/tables/{tableId}/records)
- get_by_id: Get a record (GET /api/v2/tables/{tableId}/records/{recordId})
- create: Create records (POST /api/v2/tables/{tableId}/records)
- patch_records: Update records (PATCH /api/v2/tables/{tableId}/records)
- delete_records: Delete records (DELETE /api/v2/tables/{tableId}/records)
- list_columns: List columns (GET /api/v2/meta/tables/{tableId}/columns)

## Fields

- Field values are dynamic based on table schema
- `where`: string [OPTIONAL for list] (filter condition)
- `sort`: string [OPTIONAL] (sort expression)
- `limit`: integer [OPTIONAL]
- `offset`: integer [OPTIONAL]

## Example Request Bodies

**Create Records:**
```json
[{"Name": "Alice Johnson", "Email": "alice@example.com", "Status": "Active"}]
```

**Update Records:**
```json
[{"Id": 1, "Status": "Inactive", "Notes": "Account deactivated per request"}]
```
