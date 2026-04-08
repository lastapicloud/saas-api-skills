---
name: tettra-wiki
description: Manage pages and categories via Tettra knowledge base. Use when the user
  mentions tettra, wiki, knowledge base, page, category.
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

- `title`: string [REQUIRED for create]
- `content`: string [OPTIONAL]
- `categoryId`: string [OPTIONAL]
- `query`: string [REQUIRED for search]

## Example Request Bodies

**Create Page:**
```json
{"title": "API Guidelines", "content": "All APIs must follow REST conventions.", "categoryId": "cat-123"}
```

**Search (query params):**
```json
{"query": "deployment process"}
```
