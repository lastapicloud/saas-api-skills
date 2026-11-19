---
name: swiftype-search
description: 'Manage search engines and documents via Swiftype. Use when the user
  mentions swiftype, search, site search, engine, document, crawler.

  '
version: 1.0.0
skill_type: external
base_url_env: SWIFTYPE_BASE_URL
auth_env_var: SWIFTYPE_API_KEY
auth_type: bearer
triggers:
  - swiftype
  - search
  - site search
  - engine
  - document
  - crawler
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SWIFTYPE_BASE_URL and SWIFTYPE_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Swiftype-Search

Manage search engines and documents via Swiftype. Use when the user mentions swiftype, search, site search, engine, document, crawler.


## API Endpoints

- **GET** `/api/v1/engines` - List engines
- **POST** `/api/v1/engines` - Create engine
- **GET** `/api/v1/engines/{engine_slug}` - Get engine
- **DELETE** `/api/v1/engines/{engine_slug}` - Delete engine
- **POST** `/api/v1/engines/{engine_slug}/document_types/{doc_type}/documents` - Create document
- **GET** `/api/v1/engines/{engine_slug}/document_types/{doc_type}/documents` - List documents
- **GET** `/api/v1/engines/{engine_slug}/search` - Search

## Actions

- list: List engines (GET /api/v1/engines)
- create: Create engine (POST /api/v1/engines)
- get_by_id: Get engine (GET /api/v1/engines/{engine_slug})
- delete: Delete engine (DELETE /api/v1/engines/{engine_slug})
- create_document: Create document (POST /api/v1/engines/{engine_slug}/document_types/{doc_type}/documents)
- list_documents: List documents (GET /api/v1/engines/{engine_slug}/document_types/{doc_type}/documents)
- search: Search (GET /api/v1/engines/{engine_slug}/search)

## Fields

- `name`: string [REQUIRED for create] — Display name
- `q`: string [REQUIRED for search] — Q
- `external_id`: string [REQUIRED for create_document] — External unique identifier

## Example Request Bodies

**Create Engine:**
```json
{"name": "my-site-search"}
```

**Search (query params):**
```json
{"q": "python REST API"}
```

## Response

**Engine object:**
- `id`: string — Unique engine identifier
- `name`: string — Engine name or title
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
