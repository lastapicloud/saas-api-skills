---
name: gitbook-docs
description: Manage spaces and pages via GitBook. Use when the user mentions gitbook,
  documentation, docs, space, page, wiki.
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
- list_content: List pages (GET /v1/spaces/{spaceId}/content)
- get_by_id_path: Get page (GET /v1/spaces/{spaceId}/content/path/{pagePath})
- create: Create page (POST /v1/spaces/{spaceId}/content)
- update: Update page (PUT /v1/spaces/{spaceId}/content/path/{pagePath})
- list_orgs: List organizations (GET /v1/orgs)
- search: Search content (POST /v1/spaces/{spaceId}/search)

## Fields

- `title`: string [REQUIRED for create]
- `document`: object [OPTIONAL] (page content)
- `query`: string [REQUIRED for search]

## Example Request Bodies

**Create Page:**
```json
{"title": "API Reference", "document": {"markdown": "# API Reference\nDocumentation for the REST API."}}
```

**Search Content:**
```json
{"query": "authentication setup"}
