---
name: supabase-data
description: 'Query and manage data in Supabase tables via the PostgREST API. Use
  when the user mentions supabase, database, table, query, row, record.

  '
version: 1.0.0
skill_type: external
base_url_env: SUPABASE_BASE_URL
auth_env_var: SUPABASE_SERVICE_KEY
auth_type: bearer
triggers:
  - supabase
  - database
  - table
  - query
  - row
  - record
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SUPABASE_BASE_URL and SUPABASE_SERVICE_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Supabase-Data

Query and manage data in Supabase tables via the PostgREST API. Use when the user mentions supabase, database, table, query, row, record.


## API Endpoints

- **GET** `/rest/v1/{table}` - List records from a table
- **GET** `/rest/v1/{table}?id=eq.{id}` - Get a single record
- **POST** `/rest/v1/{table}` - Create a record
- **PATCH** `/rest/v1/{table}?id=eq.{id}` - Update a record
- **DELETE** `/rest/v1/{table}?id=eq.{id}` - Delete a record
- **POST** `/rest/v1/rpc/{function_name}` - Call a database function
- **GET** `/v1/projects/:ref/endpoints/logs.all`
- **GET** `/v1/projects/:ref/endpoints/usage.api-counts`
- **GET** `/v1/projects/:ref/endpoints/usage.api-requests-count`
- **GET** `/v1/projects/:ref/database/context`
- **POST** `/v1/projects/:ref/config/custom-hostname/initialize`
- **POST** `/v1/projects/:ref/config/custom-hostname/reverify`
- **DELETE** `/v1/projects/:ref/config/custom-hostname`
- **GET** `/v1/projects/:ref/config/vanity-subdomain`

## Actions

- get_by_id: List records from a table (GET /rest/v1/{table})
- get_single_record: Get a single record (GET /rest/v1/{table}?id=eq.{id})
- add: Create a record (POST /rest/v1/{table})
- update: Update a record (PATCH /rest/v1/{table}?id=eq.{id})
- delete: Delete a record (DELETE /rest/v1/{table}?id=eq.{id})
- add_rpc: Call a database function (POST /rest/v1/rpc/{function_name})
- list: GET /v1/projects/:ref/endpoints/logs.all (GET /v1/projects/:ref/endpoints/logs.all)
- list_usage_api_counts: GET /v1/projects/:ref/endpoints/usage.api-counts (GET /v1/projects/:ref/endpoints/usage.api-counts)
- list_usage_api_requests_count: GET /v1/projects/:ref/endpoints/usage.api-requests-count (GET /v1/projects/:ref/endpoints/usage.api-requests-count)
- list_context: GET /v1/projects/:ref/database/context (GET /v1/projects/:ref/database/context)
- create: POST /v1/projects/:ref/config/custom-hostname/initialize (POST /v1/projects/:ref/config/custom-hostname/initialize)
- create_reverify: POST /v1/projects/:ref/config/custom-hostname/reverify (POST /v1/projects/:ref/config/custom-hostname/reverify)
- delete_custom_hostname: DELETE /v1/projects/:ref/config/custom-hostname (DELETE /v1/projects/:ref/config/custom-hostname)
- list_vanity_subdomain: GET /v1/projects/:ref/config/vanity-subdomain (GET /v1/projects/:ref/config/vanity-subdomain)

## Fields

- `table`: string [REQUIRED for list_records, get_record, create_record, update_record, delete_record] (table name) — Table
- `id`: string [REQUIRED for get_record, update_record, delete_record] (record ID) — Unique identifier
- `function_name`: string [REQUIRED for rpc_call] (database function name) — Function display name
- `select`: string [OPTIONAL] (column selection, e.g. "id,name") — Select
- `order`: string [OPTIONAL] (ordering, e.g. "created_at.desc") — Order
- `limit`: integer [OPTIONAL] (max records to return) — Maximum number of results

## Example Request Bodies

**Create Record:**
```json
{"name": "Test Record", "status": "active", "value": 42}
```

**RPC Call:**
```json
{"param1": "value1", "param2": 100}
```

## Response

**Rest object:**
- `id`: string — Unique rest identifier
- `name`: string — Rest name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "table": "example_table",
  "id": "example_id",
  "function_name": "example_function_name"
}
```


**Required fields reference:**
```json
{
  "table": "example_table",
  "id": "example_id",
  "function_name": "example_function_name"
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
