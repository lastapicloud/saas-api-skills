---
name: outline-wiki
description: 'Manage Outline wiki documents and collections. Use when the user mentions
  outline, wiki, document, collection, knowledge base.

  '
version: 1.0.0
skill_type: external
base_url_env: OUTLINE_BASE_URL
auth_env_var: OUTLINE_API_TOKEN
auth_type: bearer
triggers:
  - outline
  - wiki
  - document
  - collection
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

# Outline-Wiki

Manage Outline wiki documents and collections. Use when the user mentions outline, wiki, document, collection, knowledge base.


## API Endpoints

- **POST** `/api/documents.list` - List documents
- **POST** `/api/documents.info` - Get a document
- **POST** `/api/documents.create` - Create a document
- **POST** `/api/documents.update` - Update a document
- **POST** `/api/documents.delete` - Delete a document
- **POST** `/api/documents.search` - Search documents
- **POST** `/api/collections.list` - List collections
- **POST** `/api/collections.create` - Create a collection
- **POST** `/api/users.list` - List users
- **POST** `/api/auth.info` - Get current user/team info

## Actions

- create: List documents (POST /api/documents.list)
- get_document: Get a document (POST /api/documents.info)
- create_document: Create a document (POST /api/documents.create)
- update_document: Update a document (POST /api/documents.update)
- delete_document: Delete a document (POST /api/documents.delete)
- search: Search documents (POST /api/documents.search)
- list_collections: List collections (POST /api/collections.list)
- create_collection: Create a collection (POST /api/collections.create)
- list_users: List users (POST /api/users.list)
- get_current_userteam_info: Get current user/team info (POST /api/auth.info)

## Fields

- `title`: string [REQUIRED for create] — Title or heading
- `text`: string [REQUIRED for create] (markdown content) — Text content
- `collectionId`: string [REQUIRED for create] — Collection unique identifier
- `parentDocumentId`: string [OPTIONAL] — Parentdocument unique identifier
- `publish`: boolean [OPTIONAL] — Whether publish is enabled
- `query`: string [REQUIRED for search] — Search or filter query

## Example Request Bodies

**Create a Document:**
```json
{
  "title": "Engineering Runbook",
  "text": "# Runbook\nSteps for incident response and recovery.",
  "collectionId": "col_xyz789",
  "publish": true
}
```

**Update a Document:**
```json
{
  "title": "Engineering Runbook v2",
  "text": "# Runbook\nUpdated incident response procedures."
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
