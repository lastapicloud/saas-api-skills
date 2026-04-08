---
name: outline-wiki
description: Manage Outline wiki documents and collections. Use when the user mentions
  outline, wiki, document, collection, knowledge base.
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
- create_documents_info: Get a document (POST /api/documents.info)
- create_documents_create: Create a document (POST /api/documents.create)
- create_documents_update: Update a document (POST /api/documents.update)
- create_documents_delete: Delete a document (POST /api/documents.delete)
- search: Search documents (POST /api/documents.search)
- create_collections_list: List collections (POST /api/collections.list)
- create_collections_create: Create a collection (POST /api/collections.create)
- create_users_list: List users (POST /api/users.list)
- create_auth_info: Get current user/team info (POST /api/auth.info)

## Fields

- `title`: string [REQUIRED for create]
- `text`: string [REQUIRED for create] (markdown content)
- `collectionId`: string [REQUIRED for create]
- `parentDocumentId`: string [OPTIONAL]
- `publish`: boolean [OPTIONAL]
- `query`: string [REQUIRED for search]

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
