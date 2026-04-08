---
name: swiftype-search
description: Manage search engines and documents via Swiftype. Use when the user mentions
  swiftype, search, site search, engine, document, crawler.
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
- create_documents: Create document (POST /api/v1/engines/{engine_slug}/document_types/{doc_type}/documents)
- list_documents: List documents (GET /api/v1/engines/{engine_slug}/document_types/{doc_type}/documents)
- search: Search (GET /api/v1/engines/{engine_slug}/search)

## Fields

- `name`: string [REQUIRED for create]
- `q`: string [REQUIRED for search]
- `external_id`: string [REQUIRED for create_document]

## Example Request Bodies

**Create Engine:**
```json
{"name": "my-site-search"}
```

**Search (query params):**
```json
{"q": "python REST API"}
```
