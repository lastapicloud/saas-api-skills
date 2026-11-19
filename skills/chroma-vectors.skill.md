---
name: chroma-vectors
description: 'Manage Chroma vector collections and embeddings. Use when the user mentions
  chroma, chromadb, vector, embedding, collection.

  '
version: 1.0.0
skill_type: external
base_url_env: CHROMA_BASE_URL
auth_env_var: CHROMA_API_TOKEN
auth_type: header
triggers:
  - chroma
  - chromadb
  - vector
  - embedding
  - collection
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CHROMA_BASE_URL and CHROMA_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Chroma-Vectors

Manage Chroma vector collections and embeddings. Use when the user mentions chroma, chromadb, vector, embedding, collection.


## API Endpoints

- **GET** `/api/v1/collections` - List collections
- **POST** `/api/v1/collections` - Create a collection
- **GET** `/api/v1/collections/{collectionId}` - Get a collection
- **DELETE** `/api/v1/collections/{collectionName}` - Delete a collection
- **POST** `/api/v1/collections/{collectionId}/add` - Add documents
- **POST** `/api/v1/collections/{collectionId}/query` - Query collection
- **POST** `/api/v1/collections/{collectionId}/get` - Get documents
- **POST** `/api/v1/collections/{collectionId}/update` - Update documents
- **POST** `/api/v1/collections/{collectionId}/delete` - Delete documents
- **GET** `/api/v1/heartbeat` - Health check

## Actions

- list: List collections (GET /api/v1/collections)
- create: Create a collection (POST /api/v1/collections)
- get_by_id: Get a collection (GET /api/v1/collections/{collectionId})
- delete: Delete a collection (DELETE /api/v1/collections/{collectionName})
- add_documents: Add documents (POST /api/v1/collections/{collectionId}/add)
- query: Query collection (POST /api/v1/collections/{collectionId}/query)
- get_documents: Get documents (POST /api/v1/collections/{collectionId}/get)
- update_documents: Update documents (POST /api/v1/collections/{collectionId}/update)
- delete_documents: Delete documents (POST /api/v1/collections/{collectionId}/delete)
- get_health_check: Health check (GET /api/v1/heartbeat)

## Fields

- `name`: string [REQUIRED for create collection] — Display name
- `ids`: array [REQUIRED for add/update/get] — List of ids
- `documents`: array [OPTIONAL for add] (text documents) — List of documents
- `embeddings`: array [OPTIONAL for add] (vector embeddings) — List of embeddings
- `metadatas`: array [OPTIONAL for add] — List of metadatas
- `query_embeddings`: array [REQUIRED for query] — List of query embeddings
- `n_results`: integer [OPTIONAL for query] — N Results value

## Example Request Bodies

**Add Documents:**
```json
{"ids": ["doc-1", "doc-2"], "documents": ["The quick brown fox jumps over the lazy dog.", "Machine learning is a subset of AI."], "metadatas": [{"source": "wiki"}, {"source": "textbook"}]}
```

**Query Collection:**
```json
{"query_embeddings": [[0.12, -0.34, 0.56, 0.78]], "n_results": 5}
```

## Response

**Collection object:**
- `id`: string — Unique collection identifier
- `name`: string — Collection name or title
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
