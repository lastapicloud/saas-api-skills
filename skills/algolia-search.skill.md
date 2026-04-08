---
name: algolia-search
description: Search indexes and manage records via the Algolia Search API. Use when
  the user mentions algolia, search, index, record, facet.
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

- `index_name`: string [REQUIRED for search_index, add_records, get_record, delete_record, update_settings] (index name)
- `object_id`: string [REQUIRED for get_record, delete_record] (record object ID)
- `query`: string [REQUIRED for search_index] (search query)
- `requests`: array [REQUIRED for add_records] (batch operation requests)
- `searchableAttributes`: array [OPTIONAL for update_settings] (attributes to search)
- `hitsPerPage`: integer [OPTIONAL for search_index] (results per page)
- `filters`: string [OPTIONAL for search_index] (filter expression)

## Example Request Bodies

**Search Index:**
```json
{"query": "test query", "hitsPerPage": 20}
```

**Add Records (Batch):**
```json
{"requests": [{"action": "addObject", "body": {"objectID": "1", "name": "Test Record"}}]}
```
