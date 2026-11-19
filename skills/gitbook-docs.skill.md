---
name: gitbook-docs
description: 'Manage spaces and pages via GitBook. Use when the user mentions gitbook,
  documentation, docs, space, page, wiki.

  '
version: 1.0.0
skill_type: external
base_url_env: GITBOOK_BASE_URL
auth_env_var: GITBOOK_API_TOKEN
auth_type: bearer
triggers:
  - gitbook
  - documentation
  - docs
  - space
  - page
  - wiki
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GITBOOK_BASE_URL and GITBOOK_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Gitbook-Docs

Manage spaces and pages via GitBook. Use when the user mentions gitbook, documentation, docs, space, page, wiki.


## API Endpoints

- **GET** `/v1/spaces` - List spaces
- **GET** `/v1/spaces/{spaceId}` - Get space
- **GET** `/v1/spaces/{spaceId}/content` - List pages
- **GET** `/v1/spaces/{spaceId}/content/path/{pagePath}` - Get page
- **POST** `/v1/spaces/{spaceId}/content` - Create page
- **PUT** `/v1/spaces/{spaceId}/content/path/{pagePath}` - Update page
- **GET** `/v1/orgs` - List organizations
- **POST** `/v1/spaces/{spaceId}/search` - Search content

## Actions

- list: List spaces (GET /v1/spaces)
- get_by_id: Get space (GET /v1/spaces/{spaceId})
- list_pages: List pages (GET /v1/spaces/{spaceId}/content)
- get_page: Get page (GET /v1/spaces/{spaceId}/content/path/{pagePath})
- create: Create page (POST /v1/spaces/{spaceId}/content)
- update: Update page (PUT /v1/spaces/{spaceId}/content/path/{pagePath})
- list_organizations: List organizations (GET /v1/orgs)
- search: Search content (POST /v1/spaces/{spaceId}/search)

## Fields

- `title`: string [REQUIRED for create] — Title or heading
- `document`: object [OPTIONAL] (page content) — Document configuration
- `query`: string [REQUIRED for search] — Search or filter query

## Example Request Bodies

**Create Page:**
```json
{"title": "API Reference", "document": {"markdown": "# API Reference\nDocumentation for the REST API."}}
```

**Search Content:**
```json
{"query": "authentication setup"}

## Response

**Space object:**
- `id`: string — Unique space identifier
- `name`: string — Space name or title
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
