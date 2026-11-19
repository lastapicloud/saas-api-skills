---
name: coveo-search
description: 'Manage search indexes and queries via Coveo. Use when the user mentions
  coveo, search, index, query, relevance.

  '
version: 1.0.0
skill_type: external
base_url_env: COVEO_BASE_URL
auth_env_var: COVEO_API_KEY
auth_type: bearer
triggers:
  - coveo
  - search
  - index
  - query
  - relevance
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires COVEO_BASE_URL and COVEO_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Coveo-Search

Manage search indexes and queries via Coveo. Use when the user mentions coveo, search, index, query, relevance.


## API Endpoints

- **POST** `/rest/search/v2` - Execute a search query
- **GET** `/rest/organizations/{orgId}/sources` - List sources
- **POST** `/rest/organizations/{orgId}/sources` - Create a source
- **POST** `/push/v1/organizations/{orgId}/sources/{sourceId}/documents` - Push a document
- **DELETE** `/push/v1/organizations/{orgId}/sources/{sourceId}/documents` - Delete a document
- **GET** `/rest/organizations/{orgId}/machinelearning/models` - List ML models
- **GET** `/rest/search/v2/facet` - Get facet values

## Actions

- create: Execute a search query (POST /rest/search/v2)
- list: List sources (GET /rest/organizations/{orgId}/sources)
- create_source: Create a source (POST /rest/organizations/{orgId}/sources)
- create_push_document: Push a document (POST /push/v1/organizations/{orgId}/sources/{sourceId}/documents)
- delete_documents: Delete a document (DELETE /push/v1/organizations/{orgId}/sources/{sourceId}/documents)
- list_ml_models: List ML models (GET /rest/organizations/{orgId}/machinelearning/models)
- get_facet_values: Get facet values (GET /rest/search/v2/facet)

## Fields

- `q`: string [REQUIRED for search] — Q
- `documentId`: string [REQUIRED for push/delete] — Document unique identifier
- `title`: string [OPTIONAL] — Title or heading

## Example Request Bodies

**Search Query:**
```json
{"q": "machine learning best practices", "numberOfResults": 10}
```

**Push Document:**
```json
{"documentId": "https://example.com/doc/123", "title": "ML Best Practices", "data": "Full document content here"}

## Response

**Source object:**
- `id`: string — Unique source identifier
- `name`: string — Source name or title
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
