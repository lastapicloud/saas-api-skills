---
name: readme-docs
description: Manage API documentation via ReadMe. Use when the user mentions readme,
  api documentation, docs, changelog, guide.
version: 1.0.0
skill_type: external
base_url_env: README_BASE_URL
auth_env_var: README_API_KEY
auth_type: basic
triggers:
  - readme
  - api documentation
  - docs
  - changelog
  - guide
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires README_BASE_URL and README_API_KEY environment variables.
---

# Readme-Docs

Manage API documentation via ReadMe. Use when the user mentions readme, api documentation, docs, changelog, guide.

## API Endpoints

- **GET** `/v1/api-specification` - List API specs
- **POST** `/v1/api-specification` - Upload API spec
- **GET** `/v1/categories` - List categories
- **POST** `/v1/categories` - Create category
- **GET** `/v1/docs/{slug}` - Get doc
- **POST** `/v1/docs` - Create doc
- **PUT** `/v1/docs/{slug}` - Update doc
- **DELETE** `/v1/docs/{slug}` - Delete doc
- **POST** `/docs/search` - Search docs
- **PUT** `/docs/{slug}` - Update doc
- **GET** `/docs/{slug}` - Get doc
- **DELETE** `/docs/{slug}` - Delete doc
- **GET** `/changelogs` - Get changelogs
- **POST** `/changelogs` - Create changelog
- **PUT** `/changelogs/{slug}` - Update changelog

## Actions

- list: List API specs (GET /v1/api-specification)
- create: Upload API spec (POST /v1/api-specification)
- list_categories: List categories (GET /v1/categories)
- create_categories: Create category (POST /v1/categories)
- get_by_id: Get doc (GET /v1/docs/{slug})
- create_docs: Create doc (POST /v1/docs)
- update: Update doc (PUT /v1/docs/{slug})
- delete: Delete doc (DELETE /v1/docs/{slug})
- search: Search docs (POST /docs/search)
- update_docs: Update doc (PUT /docs/{slug})
- get_by_id_docs: Get doc (GET /docs/{slug})
- delete_docs: Delete doc (DELETE /docs/{slug})
- list_changelogs: Get changelogs (GET /changelogs)
- create_changelogs: Create changelog (POST /changelogs)
- update_changelogs: Update changelog (PUT /changelogs/{slug})

## Fields

- `title`: string [REQUIRED for create]
- `body`: string [OPTIONAL]
- `category`: string [REQUIRED for create]
- `slug`: string [OPTIONAL]

## Example Request Bodies

**Create Doc:**
```json
{"title": "Getting Started", "body": "# Welcome\nThis guide walks you through setup.", "category": "6489abc123def"}
```

**Update Doc:**
```json
{"title": "Getting Started (Updated)", "body": "# Welcome\nRevised setup instructions."}
```
