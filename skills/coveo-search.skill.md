---
name: coveo-search
description: Manage search indexes and queries via Coveo. Use when the user mentions
  coveo, search, index, query, relevance.
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
- create_sources: Create a source (POST /rest/organizations/{orgId}/sources)
- create_documents: Push a document (POST /push/v1/organizations/{orgId}/sources/{sourceId}/documents)
- delete_documents: Delete a document (DELETE /push/v1/organizations/{orgId}/sources/{sourceId}/documents)
- list_models: List ML models (GET /rest/organizations/{orgId}/machinelearning/models)
- list_facet: Get facet values (GET /rest/search/v2/facet)

## Fields

- `q`: string [REQUIRED for search]
- `documentId`: string [REQUIRED for push/delete]
- `title`: string [OPTIONAL]

## Example Request Bodies

**Search Query:**
```json
{"q": "machine learning best practices", "numberOfResults": 10}
```

**Push Document:**
```json
{"documentId": "https://example.com/doc/123", "title": "ML Best Practices", "data": "Full document content here"}
