---
name: doofinder-search
description: Manage search indexes and queries via Doofinder. Use when the user mentions
  doofinder, search, ecommerce search, product search, index.
version: 1.0.0
skill_type: external
base_url_env: DOOFINDER_BASE_URL
auth_env_var: DOOFINDER_API_KEY
auth_type: header
triggers:
  - doofinder
  - search
  - ecommerce search
  - product search
  - index
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires DOOFINDER_BASE_URL and DOOFINDER_API_KEY environment variables.
---

# Doofinder-Search

Manage search indexes and queries via Doofinder. Use when the user mentions doofinder, search, ecommerce search, product search, index.

## API Endpoints

- **GET** `/v2/search` - Execute a search query
- **GET** `/v2/search-engines` - List search engines
- **POST** `/v2/search-engines` - Create a search engine
- **GET** `/v2/search-engines/{hashid}/indices` - List indices
- **POST** `/v2/search-engines/{hashid}/indices/{name}/items` - Index items
- **DELETE** `/v2/search-engines/{hashid}/indices/{name}/items/{id}` - Delete an item
- **POST** `/v2/search-engines/{hashid}/indices/{name}/_reindex` - Reindex
- **GET** `/v2/search-engines/{hashid}/stats` - Get search stats

## Actions

- search: Execute a search query (GET /v2/search)
- search_search_engines: List search engines (GET /v2/search-engines)
- search_search_engines_2: Create a search engine (POST /v2/search-engines)
- list: List indices (GET /v2/search-engines/{hashid}/indices)
- create: Index items (POST /v2/search-engines/{hashid}/indices/{name}/items)
- delete: Delete an item (DELETE /v2/search-engines/{hashid}/indices/{name}/items/{id})
- create__reindex: Reindex (POST /v2/search-engines/{hashid}/indices/{name}/_reindex)
- list_stats: Get search stats (GET /v2/search-engines/{hashid}/stats)

## Fields

- `query`: string [REQUIRED for search]
- `hashid`: string [REQUIRED]
- `items`: array [REQUIRED for index_items]

## Example Request Bodies

**Search Query (query parameters):**
```json
{"query": "wireless headphones", "hashid": "abc123def456", "rpp": 10}
```

**Index Items:**
```json
{"items": [{"id": "prod-001", "title": "Wireless Headphones", "price": 79.99, "category": "Electronics"}]}
```
