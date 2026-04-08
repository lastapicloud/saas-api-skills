---
name: opensearch-search
description: Manage indices and documents via OpenSearch. Use when the user mentions
  opensearch, search, index, document, query, analytics.
version: 1.0.0
skill_type: external
base_url_env: OPENSEARCH_BASE_URL
auth_env_var: OPENSEARCH_API_KEY
auth_user_env: OPENSEARCH_USERNAME
auth_type: basic
triggers:
  - opensearch
  - search
  - index
  - document
  - query
  - analytics
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires OPENSEARCH_BASE_URL and OPENSEARCH_API_KEY environment variables.
---

# Opensearch-Search

Manage indices and documents via OpenSearch. Use when the user mentions opensearch, search, index, document, query, analytics.

## API Endpoints

- **GET** `/_cat/indices` - List indices
- **PUT** `/{index}` - Create index
- **DELETE** `/{index}` - Delete index
- **POST** `/{index}/_doc` - Index document
- **GET** `/{index}/_doc/{id}` - Get document
- **DELETE** `/{index}/_doc/{id}` - Delete document
- **POST** `/{index}/_search` - Search documents
- **POST** `/_bulk` - Bulk operations

## Actions

- list: List indices (GET /_cat/indices)
- update: Create index (PUT /{index})
- delete: Delete index (DELETE /{index})
- create: Index document (POST /{index}/_doc)
- get_by_id: Get document (GET /{index}/_doc/{id})
- delete__doc: Delete document (DELETE /{index}/_doc/{id})
- search: Search documents (POST /{index}/_search)
- create__bulk: Bulk operations (POST /_bulk)

## Fields

- `index`: string [REQUIRED]
- `query`: object [REQUIRED for search]
- `mappings`: object [OPTIONAL for create_index]

## Example Request Bodies

**Index Document:**
```json
{"title": "Getting Started Guide", "content": "This guide covers the basics of using the platform.", "tags": ["guide", "onboarding"], "created_at": "2024-03-15"}
```

**Search Documents:**
```json
{"query": {"bool": {"must": [{"match": {"content": "deployment"}}], "filter": [{"term": {"tags": "guide"}}]}}}
```
