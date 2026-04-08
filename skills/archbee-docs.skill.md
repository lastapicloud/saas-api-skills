---
name: archbee-docs
description: Manage documentation spaces and pages via Archbee. Use when the user
  mentions archbee, documentation, docs, wiki, knowledge base.
version: 1.0.0
skill_type: external
base_url_env: ARCHBEE_BASE_URL
auth_env_var: ARCHBEE_API_KEY
auth_type: header
triggers:
  - archbee
  - documentation
  - docs
  - wiki
  - knowledge base
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ARCHBEE_BASE_URL and ARCHBEE_API_KEY environment variables.
---

# Archbee-Docs

Manage documentation spaces and pages via Archbee. Use when the user mentions archbee, documentation, docs, wiki, knowledge base.

## API Endpoints

- **GET** `/v1/spaces` - List spaces
- **GET** `/v1/spaces/{spaceId}` - Get space details
- **GET** `/v1/spaces/{spaceId}/documents` - List documents in a space
- **POST** `/v1/documents` - Create a document
- **GET** `/v1/documents/{documentId}` - Get document by ID
- **PUT** `/v1/documents/{documentId}` - Update a document
- **DELETE** `/v1/documents/{documentId}` - Delete a document
- **GET** `/v1/search` - Search documents

## Actions

- list: List spaces (GET /v1/spaces)
- get_by_id: Get space details (GET /v1/spaces/{spaceId})
- list_documents: List documents in a space (GET /v1/spaces/{spaceId}/documents)
- create: Create a document (POST /v1/documents)
- get_by_id_documents: Get document by ID (GET /v1/documents/{documentId})
- update: Update a document (PUT /v1/documents/{documentId})
- delete: Delete a document (DELETE /v1/documents/{documentId})
- search: Search documents (GET /v1/search)

## Fields

- `title`: string [REQUIRED for create]
- `content`: string [OPTIONAL]
- `spaceId`: string [REQUIRED for create]

## Example Request Bodies

**Create Document:**
```json
{"title": "Getting Started Guide", "spaceId": "space_abc123", "content": "Welcome to our documentation."}
```

**Update Document:**
```json
{"title": "Updated Getting Started Guide", "content": "Revised documentation content."}
