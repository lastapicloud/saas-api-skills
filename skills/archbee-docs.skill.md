---
name: archbee-docs
description: 'Manage documentation spaces and pages via Archbee. Use when the user
  mentions archbee, documentation, docs, wiki, knowledge base.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
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
- list_documents_space: List documents in a space (GET /v1/spaces/{spaceId}/documents)
- create: Create a document (POST /v1/documents)
- get_document_id: Get document by ID (GET /v1/documents/{documentId})
- update: Update a document (PUT /v1/documents/{documentId})
- delete: Delete a document (DELETE /v1/documents/{documentId})
- search: Search documents (GET /v1/search)

## Fields

- `title`: string [REQUIRED for create] — Title or heading
- `content`: string [OPTIONAL] — Content body
- `spaceId`: string [REQUIRED for create] — Space unique identifier

## Example Request Bodies

**Create Document:**
```json
{"title": "Getting Started Guide", "spaceId": "space_abc123", "content": "Welcome to our documentation."}
```

**Update Document:**
```json
{"title": "Updated Getting Started Guide", "content": "Revised documentation content."}

## Response

**Document object:**
- `id`: string — Unique document identifier
- `name`: string — Document name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 404 | Resource not found — check the ID or identifier |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
