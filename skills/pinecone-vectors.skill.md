---
name: pinecone-vectors
description: Manage vector indexes and perform similarity searches via the Pinecone
  API. Use when the user mentions pinecone, vector, embedding, similarity, search
  vectors.
version: 1.0.0
skill_type: external
base_url_env: PINECONE_BASE_URL
auth_env_var: PINECONE_API_KEY
auth_type: header
triggers:
  - pinecone
  - vector
  - embedding
  - similarity
  - search vectors
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PINECONE_BASE_URL and PINECONE_API_KEY environment variables.
---

# Pinecone-Vectors

Manage vector indexes and perform similarity searches via the Pinecone API. Use when the user mentions pinecone, vector, embedding, similarity, search vectors.

## API Endpoints

- **GET** `/indexes` - List all indexes
- **POST** `/vectors/upsert` - Upsert vectors into an index
- **POST** `/query` - Query vectors by similarity
- **GET** `/vectors/fetch` - Fetch vectors by ID
- **POST** `/vectors/delete` - Delete vectors
- **GET** `/indexes/{index_name}` - Describe an index
- **POST** `/indexes` - Create index
- **PATCH** `/indexes/{indexName}` - Configure index
- **DELETE** `/indexes/{indexName}` - Delete Index
- **GET** `/bulk/imports` - List imports
- **POST** `/bulk/imports` - Start import
- **GET** `/bulk/imports/{id}` - Describe an import
- **DELETE** `/bulk/imports/{id}` - Cancel an import
- **GET** `/collections` - List collections
- **POST** `/collections` - Create collection

## Actions

- list: List all indexes (GET /indexes)
- create: Upsert vectors into an index (POST /vectors/upsert)
- query: Query vectors by similarity (POST /query)
- list_fetch: Fetch vectors by ID (GET /vectors/fetch)
- create_delete: Delete vectors (POST /vectors/delete)
- get_by_id: Describe an index (GET /indexes/{index_name})
- create_indexes: Create index (POST /indexes)
- update: Configure index (PATCH /indexes/{indexName})
- delete: Delete Index (DELETE /indexes/{indexName})
- list_imports: List imports (GET /bulk/imports)
- create_imports: Start import (POST /bulk/imports)
- get_by_id_imports: Describe an import (GET /bulk/imports/{id})
- delete_imports: Cancel an import (DELETE /bulk/imports/{id})
- list_collections: List collections (GET /collections)
- create_collections: Create collection (POST /collections)

## Fields

- `index_name`: string [REQUIRED for describe_index] (index name)
- `vectors`: array [REQUIRED for upsert_vectors] (list of vector objects with id, values, metadata)
- `vector`: array [REQUIRED for query_vectors] (query vector values)
- `top_k`: integer [REQUIRED for query_vectors] (number of results to return)
- `namespace`: string [OPTIONAL] (namespace for vector operations)
- `ids`: array [REQUIRED for fetch_vectors, delete_vectors] (vector IDs)
- `filter`: object [OPTIONAL for query_vectors] (metadata filter)

## Example Request Bodies

**Upsert Vectors:**
```json
{"vectors": [{"id": "vec1", "values": [0.1, 0.2, 0.3], "metadata": {"category": "test"}}], "namespace": "default"}
```

**Query Vectors:**
```json
{"vector": [0.1, 0.2, 0.3], "top_k": 10, "namespace": "default"}
```
