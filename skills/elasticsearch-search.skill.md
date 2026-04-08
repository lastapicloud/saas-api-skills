---
name: elasticsearch-search
description: Manage Elasticsearch indexes, documents, and searches. Use when the user
  mentions elasticsearch, elastic, index, document, search, query.
version: 1.0.0
skill_type: external
base_url_env: ELASTICSEARCH_BASE_URL
auth_env_var: ELASTICSEARCH_API_KEY
auth_type: header
triggers:
  - elasticsearch
  - elastic
  - index
  - document
  - search
  - query
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ELASTICSEARCH_BASE_URL and ELASTICSEARCH_API_KEY environment
  variables.
---

# Elasticsearch-Search

Manage Elasticsearch indexes, documents, and searches. Use when the user mentions elasticsearch, elastic, index, document, search, query.

## API Endpoints

- **GET** `/_cat/indices` - List indexes
- **PUT** `/{index}` - Create an index
- **DELETE** `/{index}` - Delete an index
- **POST** `/{index}/_doc` - Index a document
- **GET** `/{index}/_doc/{docId}` - Get a document
- **DELETE** `/{index}/_doc/{docId}` - Delete a document
- **POST** `/{index}/_search` - Search documents
- **POST** `/{index}/_update/{docId}` - Update a document
- **POST** `/_bulk` - Bulk operations
- **GET** `/{index}/_mapping` - Get index mapping

## Actions

- list: List indexes (GET /_cat/indices)
- update: Create an index (PUT /{index})
- delete: Delete an index (DELETE /{index})
- create: Index a document (POST /{index}/_doc)
- get_by_id: Get a document (GET /{index}/_doc/{docId})
- delete__doc: Delete a document (DELETE /{index}/_doc/{docId})
- search: Search documents (POST /{index}/_search)
- create__update: Update a document (POST /{index}/_update/{docId})
- create__bulk: Bulk operations (POST /_bulk)
- list__mapping: Get index mapping (GET /{index}/_mapping)

## Fields

- `mappings`: object [OPTIONAL for create index] with `properties`
- `query`: object [REQUIRED for search] (Elasticsearch Query DSL)
- `doc`: object [REQUIRED for update]
- `size`: integer [OPTIONAL for search]
- `from`: integer [OPTIONAL for search] (offset)
- `sort`: array [OPTIONAL for search]

## Example Request Bodies

**Index Document:**
```json
{"title": "Getting Started", "content": "Welcome to our platform", "author": "admin", "created_at": "2025-01-15"}
```

**Search Documents:**
```json
{"query": {"match": {"content": "getting started"}}, "size": 10, "sort": [{"created_at": "desc"}]}
