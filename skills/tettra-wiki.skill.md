---
name: tettra-wiki
description: 'Manage pages and categories via Tettra knowledge base. Use when the
  user mentions tettra, wiki, knowledge base, page, category.

  '
version: 1.0.0
skill_type: external
base_url_env: TETTRA_BASE_URL
auth_env_var: TETTRA_API_TOKEN
auth_type: bearer
triggers:
  - tettra
  - wiki
  - knowledge base
  - page
  - category
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TETTRA_BASE_URL and TETTRA_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Tettra-Wiki

Manage pages and categories via Tettra knowledge base. Use when the user mentions tettra, wiki, knowledge base, page, category.


## API Endpoints

- **GET** `/v1/pages` - List pages
- **POST** `/v1/pages` - Create page
- **GET** `/v1/pages/{pageId}` - Get page
- **PUT** `/v1/pages/{pageId}` - Update page
- **DELETE** `/v1/pages/{pageId}` - Delete page
- **GET** `/v1/categories` - List categories
- **GET** `/v1/search` - Search pages

## Actions

- list: List pages (GET /v1/pages)
- create: Create page (POST /v1/pages)
- get_by_id: Get page (GET /v1/pages/{pageId})
- update: Update page (PUT /v1/pages/{pageId})
- delete: Delete page (DELETE /v1/pages/{pageId})
- list_categories: List categories (GET /v1/categories)
- search: Search pages (GET /v1/search)

## Fields

- `title`: string [REQUIRED for create] — Title or heading
- `content`: string [OPTIONAL] — Content body
- `categoryId`: string [OPTIONAL] — Category unique identifier
- `query`: string [REQUIRED for search] — Search or filter query

## Example Request Bodies

**Create Page:**
```json
{"title": "API Guidelines", "content": "All APIs must follow REST conventions.", "categoryId": "cat-123"}
```

**Search (query params):**
```json
{"query": "deployment process"}
```

## Response

**Page object:**
- `id`: string — Unique page identifier
- `name`: string — Page name or title
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
