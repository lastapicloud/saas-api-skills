---
name: algolia-search
description: 'Search indexes and manage records via the Algolia Search API. Use when
  the user mentions algolia, search, index, record, facet.

  '
version: 1.0.0
skill_type: external
base_url_env: ALGOLIA_BASE_URL
auth_env_var: ALGOLIA_API_KEY
auth_type: header
triggers:
  - algolia
  - search
  - index
  - record
  - facet
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ALGOLIA_BASE_URL and ALGOLIA_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Algolia-Search

Search indexes and manage records via the Algolia Search API. Use when the user mentions algolia, search, index, record, facet.


## API Endpoints

- **POST** `/indexes/{index_name}/query` - Search an index
- **POST** `/indexes/{index_name}/batch` - Add or update records in batch
- **GET** `/indexes/{index_name}/{object_id}` - Get a record by object ID
- **DELETE** `/indexes/{index_name}/{object_id}` - Delete a record
- **GET** `/indexes` - List all indexes
- **PUT** `/indexes/{index_name}/settings` - Update index settings

## Actions

- query: Search an index (POST /indexes/{index_name}/query)
- create: Add or update records in batch (POST /indexes/{index_name}/batch)
- get_by_id: Get a record by object ID (GET /indexes/{index_name}/{object_id})
- delete: Delete a record (DELETE /indexes/{index_name}/{object_id})
- list: List all indexes (GET /indexes)
- put_settings: Update index settings (PUT /indexes/{index_name}/settings)

## Fields

- `index_name`: string [REQUIRED for search_index, add_records, get_record, delete_record, update_settings] (index name) — Index display name
- `object_id`: string [REQUIRED for get_record, delete_record] (record object ID) — Object unique identifier
- `query`: string [REQUIRED for search_index] (search query) — Search or filter query
- `requests`: array [REQUIRED for add_records] (batch operation requests) — List of requests
- `searchableAttributes`: array [OPTIONAL for update_settings] (attributes to search) — List of searchableAttributes
- `hitsPerPage`: integer [OPTIONAL for search_index] (results per page) — Hitsper page number
- `filters`: string [OPTIONAL for search_index] (filter expression) — Filters

## Example Request Bodies

**Search Index:**
```json
{"query": "test query", "hitsPerPage": 20}
```

**Add Records (Batch):**
```json
{"requests": [{"action": "addObject", "body": {"objectID": "1", "name": "Test Record"}}]}
```

## Response

**Indexe object:**
- `id`: string — Unique indexe identifier
- `name`: string — Indexe name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "index_name": "example_index_name",
  "object_id": "example_object_id"
}
```


**Required fields reference:**
```json
{
  "index_name": "example_index_name",
  "object_id": "example_object_id"
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
