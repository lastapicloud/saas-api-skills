---
name: airtable-data
description: Manage Airtable bases, tables, and records. Use when the user mentions
  airtable, base, table, record, spreadsheet.
version: 1.0.0
skill_type: external
base_url_env: AIRTABLE_BASE_URL
auth_env_var: AIRTABLE_API_TOKEN
auth_type: bearer
triggers:
  - airtable
  - base
  - table
  - record
  - spreadsheet
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires AIRTABLE_BASE_URL and AIRTABLE_API_TOKEN environment variables.
---

# Airtable-Data

Manage Airtable bases, tables, and records. Use when the user mentions airtable, base, table, record, spreadsheet.

## API Endpoints

- **GET** `/v0/meta/bases` - List bases
- **GET** `/v0/meta/bases/{baseId}/tables` - List tables
- **GET** `/v0/{baseId}/{tableIdOrName}` - List records
- **GET** `/v0/{baseId}/{tableIdOrName}/{recordId}` - Get a record
- **POST** `/v0/{baseId}/{tableIdOrName}` - Create records
- **PATCH** `/v0/{baseId}/{tableIdOrName}` - Update records
- **DELETE** `/v0/{baseId}/{tableIdOrName}` - Delete records
- **POST** `/v0/meta/bases/{baseId}/tables` - Create a table
- **PATCH** `/v0/meta/bases/{baseId}/tables/{tableId}` - Update a table

## Actions

- list: List bases (GET /v0/meta/bases)
- list_tables: List tables (GET /v0/meta/bases/{baseId}/tables)
- get_by_id: List records (GET /v0/{baseId}/{tableIdOrName})
- get_by_id_v0: Get a record (GET /v0/{baseId}/{tableIdOrName}/{recordId})
- create_v0: Create records (POST /v0/{baseId}/{tableIdOrName})
- update: Update records (PATCH /v0/{baseId}/{tableIdOrName})
- delete: Delete records (DELETE /v0/{baseId}/{tableIdOrName})
- create: Create a table (POST /v0/meta/bases/{baseId}/tables)
- update_tables: Update a table (PATCH /v0/meta/bases/{baseId}/tables/{tableId})

## Fields

- `records`: array [REQUIRED for create/update] with `fields` object
- `fields`: object [REQUIRED] (key-value pairs matching column names)
- `filterByFormula`: string [OPTIONAL for list]
- `sort`: array [OPTIONAL] with `field`, `direction`
- `maxRecords`: integer [OPTIONAL]

## Example Request Bodies

**Create Records:**
```json
{"records": [{"fields": {"Name": "John Doe", "Email": "john@example.com", "Status": "Active"}}]}
```

**Update Records:**
```json
{"records": [{"id": "rec123", "fields": {"Status": "Inactive"}}]}
