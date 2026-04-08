---
name: baserow-data
description: Manage Baserow databases, tables, and rows. Use when the user mentions
  baserow, database, table, row.
version: 1.0.0
skill_type: external
base_url_env: BASEROW_BASE_URL
auth_env_var: BASEROW_API_TOKEN
auth_type: header
triggers:
  - baserow
  - database
  - table
  - row
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BASEROW_BASE_URL and BASEROW_API_TOKEN environment variables.
---

# Baserow-Data

Manage Baserow databases, tables, and rows. Use when the user mentions baserow, database, table, row.

## API Endpoints

- **GET** `/api/applications/` - List applications (databases)
- **GET** `/api/database/tables/{tableId}/` - Get table info
- **GET** `/api/database/rows/table/{tableId}/` - List rows
- **GET** `/api/database/rows/table/{tableId}/{rowId}/` - Get a row
- **POST** `/api/database/rows/table/{tableId}/` - Create a row
- **PATCH** `/api/database/rows/table/{tableId}/{rowId}/` - Update a row
- **DELETE** `/api/database/rows/table/{tableId}/{rowId}/` - Delete a row
- **GET** `/api/database/fields/table/{tableId}/` - List fields
- **POST** `/api/database/fields/table/{tableId}/` - Create a field
- **GET** `/api/database/tables/database/{databaseId}/` - List tables

## Actions

- list: List applications (databases) (GET /api/applications/)
- get_by_id: Get table info (GET /api/database/tables/{tableId}/)
- get_by_id_table: List rows (GET /api/database/rows/table/{tableId}/)
- get_by_id_table_2: Get a row (GET /api/database/rows/table/{tableId}/{rowId}/)
- add_table: Create a row (POST /api/database/rows/table/{tableId}/)
- update: Update a row (PATCH /api/database/rows/table/{tableId}/{rowId}/)
- delete: Delete a row (DELETE /api/database/rows/table/{tableId}/{rowId}/)
- get_by_id_table_3: List fields (GET /api/database/fields/table/{tableId}/)
- add_table_fields: Create a field (POST /api/database/fields/table/{tableId}/)
- get_by_id_database: List tables (GET /api/database/tables/database/{databaseId}/)

## Fields

- Field values are dynamic based on table schema (key-value pairs)
- `field_{fieldId}`: value matching the field type

## Example Request Bodies

**Create Row:**
```json
{"field_123": "John Doe", "field_124": "john@example.com", "field_125": true}
```

**Update Row:**
```json
{"field_123": "Jane Doe", "field_124": "jane@example.com"}
