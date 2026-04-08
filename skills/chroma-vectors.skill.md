---
name: chroma-vectors
description: Manage Chroma vector collections and embeddings. Use when the user mentions
  chroma, chromadb, vector, embedding, collection.
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
- create_add: Add documents (POST /api/v1/collections/{collectionId}/add)
- query: Query collection (POST /api/v1/collections/{collectionId}/query)
- create_get: Get documents (POST /api/v1/collections/{collectionId}/get)
- create_update: Update documents (POST /api/v1/collections/{collectionId}/update)
- create_delete: Delete documents (POST /api/v1/collections/{collectionId}/delete)
- list_heartbeat: Health check (GET /api/v1/heartbeat)

## Fields

- `name`: string [REQUIRED for create collection]
- `ids`: array [REQUIRED for add/update/get]
- `documents`: array [OPTIONAL for add] (text documents)
- `embeddings`: array [OPTIONAL for add] (vector embeddings)
- `metadatas`: array [OPTIONAL for add]
- `query_embeddings`: array [REQUIRED for query]
- `n_results`: integer [OPTIONAL for query]

## Example Request Bodies

**Add Documents:**
```json
{"ids": ["doc-1", "doc-2"], "documents": ["The quick brown fox jumps over the lazy dog.", "Machine learning is a subset of AI."], "metadatas": [{"source": "wiki"}, {"source": "textbook"}]}
```

**Query Collection:**
```json
{"query_embeddings": [[0.12, -0.34, 0.56, 0.78]], "n_results": 5}
```
