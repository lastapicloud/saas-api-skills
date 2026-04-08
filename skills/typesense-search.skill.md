---
name: typesense-search
description: Manage Typesense collections and search documents. Use when the user
  mentions typesense, search, collection, document, index.
version: 1.0.0
skill_type: external
base_url_env: TYPESENSE_BASE_URL
auth_env_var: TYPESENSE_API_KEY
auth_type: header
triggers:
  - typesense
  - search
  - collection
  - document
  - index
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TYPESENSE_BASE_URL and TYPESENSE_API_KEY environment variables.
---

# Typesense-Search

Manage Typesense collections and search documents. Use when the user mentions typesense, search, collection, document, index.

## API Endpoints

- **GET** `/collections` - List collections
- **POST** `/collections` - Create a collection
- **GET** `/collections/{collectionName}` - Get a collection
- **DELETE** `/collections/{collectionName}` - Delete a collection
- **POST** `/collections/{collectionName}/documents` - Create a document
- **GET** `/collections/{collectionName}/documents/{documentId}` - Get a document
- **DELETE** `/collections/{collectionName}/documents/{documentId}` - Delete a document
- **GET** `/collections/{collectionName}/documents/search` - Search documents
- **POST** `/collections/{collectionName}/documents/import` - Import documents
- **POST** `/multi_search` - Multi-collection search

## Actions

- list: List collections (GET /collections)
- create: Create a collection (POST /collections)
- get_by_id: Get a collection (GET /collections/{collectionName})
- delete: Delete a collection (DELETE /collections/{collectionName})
- create_documents: Create a document (POST /collections/{collectionName}/documents)
- get_by_id_documents: Get a document (GET /collections/{collectionName}/documents/{documentId})
- delete_documents: Delete a document (DELETE /collections/{collectionName}/documents/{documentId})
- search: Search documents (GET /collections/{collectionName}/documents/search)
- create_import: Import documents (POST /collections/{collectionName}/documents/import)
- search_multi_search: Multi-collection search (POST /multi_search)

## Fields

- `name`: string [REQUIRED for create collection]
- `fields`: array [REQUIRED for create] with `name`, `type`, `facet`
- `q`: string [REQUIRED for search] (query text)
- `query_by`: string [REQUIRED for search] (comma-separated field names)
- `filter_by`: string [OPTIONAL for search]
- `sort_by`: string [OPTIONAL for search]

## Example Request Bodies

**Create Collection:**
```json
{"name": "products", "fields": [{"name": "title", "type": "string"}, {"name": "price", "type": "float", "facet": true}]}
```

**Search (query params):**
```json
{"q": "wireless keyboard", "query_by": "title", "filter_by": "price:<100", "sort_by": "price:asc"}
```
