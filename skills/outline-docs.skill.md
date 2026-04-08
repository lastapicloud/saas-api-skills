---
name: outline-docs
description: Manage documents and collections via Outline. Use when the user mentions
  outline, docs, document, collection, wiki, knowledge base.
version: 1.0.0
skill_type: external
base_url_env: OUTLINE_BASE_URL
auth_env_var: OUTLINE_API_TOKEN
auth_type: bearer
triggers:
  - outline
  - docs
  - document
  - collection
  - wiki
  - knowledge base
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires OUTLINE_BASE_URL and OUTLINE_API_TOKEN environment variables.
---

# Outline-Docs

Manage documents and collections via Outline. Use when the user mentions outline, docs, document, collection, wiki, knowledge base.

## API Endpoints

- **POST** `/api/documents.list` - List documents
- **POST** `/api/documents.create` - Create document
- **POST** `/api/documents.info` - Get document
- **POST** `/api/documents.update` - Update document
- **POST** `/api/documents.delete` - Delete document
- **POST** `/api/documents.search` - Search documents
- **POST** `/api/collections.list` - List collections
- **POST** `/api/collections.create` - Create collection

## Actions

- create: List documents (POST /api/documents.list)
- create_documents_create: Create document (POST /api/documents.create)
- create_documents_info: Get document (POST /api/documents.info)
- create_documents_update: Update document (POST /api/documents.update)
- create_documents_delete: Delete document (POST /api/documents.delete)
- search: Search documents (POST /api/documents.search)
- create_collections_list: List collections (POST /api/collections.list)
- create_collections_create: Create collection (POST /api/collections.create)

## Fields

- `title`: string [REQUIRED for create]
- `text`: string [OPTIONAL]
- `collectionId`: string [REQUIRED for create]
- `query`: string [REQUIRED for search]

## Example Request Bodies

**Create a Document:**
```json
{
  "title": "API Integration Guide",
  "text": "# Overview\nThis document covers the API integration process.",
  "collectionId": "col_abc123",
  "publish": true
}
```

**Search Documents:**
```json
{
  "query": "integration guide"
}
```
