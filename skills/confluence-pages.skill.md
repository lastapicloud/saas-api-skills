---
name: confluence-pages
description: "Create, search, and manage Confluence pages and spaces. Use when the user mentions confluence, page, wiki, documentation, doc, space."
version: 1.0.0
skill_type: external
base_url_env: ATLASSIAN_BASE_URL
auth_env_var: ATLASSIAN_API_TOKEN
auth_user_env: ATLASSIAN_EMAIL
auth_type: basic
triggers:
  - confluence
  - page
  - wiki
  - documentation
  - doc
  - space
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ATLASSIAN_BASE_URL and ATLASSIAN_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Confluence-Pages

Create, search, and manage Confluence pages and spaces. Use when the user mentions confluence, page, wiki, documentation, doc, space.


## API Endpoints

- **GET** `/wiki/api/v2/pages` - List pages
- **GET** `/wiki/api/v2/pages/{id}` - Get a specific page
- **POST** `/wiki/api/v2/pages` - Create a new page
- **PUT** `/wiki/api/v2/pages/{id}` - Update a page
- **DELETE** `/wiki/api/v2/pages/{id}` - Delete a page
- **GET** `/wiki/api/v2/spaces` - List all spaces
- **GET** `/wiki/rest/api/content/{id}`
- **GET** `/wiki/rest/api/content`

## Actions

- list: List pages (GET /wiki/api/v2/pages)
- get_by_id: Get a specific page (GET /wiki/api/v2/pages/{id})
- create: Create a new page (POST /wiki/api/v2/pages)
- update: Update a page (PUT /wiki/api/v2/pages/{id})
- delete: Delete a page (DELETE /wiki/api/v2/pages/{id})
- list_spaces: List all spaces (GET /wiki/api/v2/spaces)
- get_by_id_content: GET /wiki/rest/api/content/{id} (GET /wiki/rest/api/content/{id})
- list_content: GET /wiki/rest/api/content (GET /wiki/rest/api/content)

## Fields

- `spaceId`: string [REQUIRED for create]
- `title`: string [REQUIRED for create]
- `parentId`: string [OPTIONAL] (parent page ID for nesting)
- `body`: object with `representation` and `value` [OPTIONAL]

## Example Request Bodies

**Create Page:**
```json
{"spaceId": "12345", "title": "Meeting Notes", "body": {"representation": "storage", "value": "Notes here"}}
```

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request — missing required field, wrong type, or constraint violation |
| 401 | Authentication failed — check API credentials |
| 403 | Forbidden — insufficient permissions |
| 404 | Resource not found |
| 429 | Rate limited — retry after delay |
| 500 | Server error |
