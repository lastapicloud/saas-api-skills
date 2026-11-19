---
name: outline-docs
description: 'Manage documents and collections via Outline. Use when the user mentions
  outline, docs, document, collection, wiki, knowledge base.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
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
- create_document: Create document (POST /api/documents.create)
- get_document: Get document (POST /api/documents.info)
- update_document: Update document (POST /api/documents.update)
- delete_document: Delete document (POST /api/documents.delete)
- search: Search documents (POST /api/documents.search)
- list_collections: List collections (POST /api/collections.list)
- create_collection: Create collection (POST /api/collections.create)

## Fields

- `title`: string [REQUIRED for create] — Title or heading
- `text`: string [OPTIONAL] — Text content
- `collectionId`: string [REQUIRED for create] — Collection unique identifier
- `query`: string [REQUIRED for search] — Search or filter query

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

## Response

**Documents.List object:**
- `id`: string — Unique documents.list identifier
- `name`: string — Documents.List name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
