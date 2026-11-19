---
name: airtable-data
description: 'Manage Airtable bases, tables, and records. Use when the user mentions
  airtable, base, table, record, spreadsheet.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
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
- get_record: Get a record (GET /v0/{baseId}/{tableIdOrName}/{recordId})
- create: Create records (POST /v0/{baseId}/{tableIdOrName})
- update: Update records (PATCH /v0/{baseId}/{tableIdOrName})
- delete: Delete records (DELETE /v0/{baseId}/{tableIdOrName})
- create_create_a: Create a table (POST /v0/meta/bases/{baseId}/tables)
- update_table: Update a table (PATCH /v0/meta/bases/{baseId}/tables/{tableId})

## Fields

- `records`: array [REQUIRED for create/update] with `fields` object — List of records
- `fields`: object [REQUIRED] (key-value pairs matching column names) — Fields configuration
- `filterByFormula`: string [OPTIONAL for list] — Filterbyformula
- `sort`: array [OPTIONAL] with `field`, `direction` — Sort order
- `maxRecords`: integer [OPTIONAL] — Maxrecords value

## Example Request Bodies

**Create Records:**
```json
{"records": [{"fields": {"Name": "John Doe", "Email": "john@example.com", "Status": "Active"}}]}
```

**Update Records:**
```json
{"records": [{"id": "rec123", "fields": {"Status": "Inactive"}}]}

## Response

**Table object:**
- `id`: string — Unique table identifier
- `name`: string — Table name or title
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
