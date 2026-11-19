---
name: zilliz-vectors
description: 'Manage Zilliz Cloud (Milvus) collections and vectors. Use when the user
  mentions zilliz, milvus, vector, embedding, collection.

  '
version: 1.0.0
skill_type: external
base_url_env: ZILLIZ_BASE_URL
auth_env_var: ZILLIZ_API_KEY
auth_type: bearer
triggers:
  - zilliz
  - milvus
  - vector
  - embedding
  - collection
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ZILLIZ_BASE_URL and ZILLIZ_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Zilliz-Vectors

Manage Zilliz Cloud (Milvus) collections and vectors. Use when the user mentions zilliz, milvus, vector, embedding, collection.


## API Endpoints

- **GET** `/v2/vectordb/collections/list` - List collections
- **POST** `/v2/vectordb/collections/create` - Create a collection
- **POST** `/v2/vectordb/collections/describe` - Describe a collection
- **POST** `/v2/vectordb/collections/drop` - Drop a collection
- **POST** `/v2/vectordb/entities/insert` - Insert vectors
- **POST** `/v2/vectordb/entities/search` - Search vectors
- **POST** `/v2/vectordb/entities/query` - Query vectors
- **POST** `/v2/vectordb/entities/delete` - Delete vectors
- **POST** `/v2/vectordb/entities/get` - Get vectors by ID
- **POST** `/v2/vectordb/indexes/create` - Create an index

## Actions

- list: List collections (GET /v2/vectordb/collections/list)
- create: Create a collection (POST /v2/vectordb/collections/create)
- create_describe_collection: Describe a collection (POST /v2/vectordb/collections/describe)
- create_drop_collection: Drop a collection (POST /v2/vectordb/collections/drop)
- create_insert_vectors: Insert vectors (POST /v2/vectordb/entities/insert)
- search: Search vectors (POST /v2/vectordb/entities/search)
- query: Query vectors (POST /v2/vectordb/entities/query)
- delete_vectors: Delete vectors (POST /v2/vectordb/entities/delete)
- get_vectors_id: Get vectors by ID (POST /v2/vectordb/entities/get)
- create_index: Create an index (POST /v2/vectordb/indexes/create)

## Fields

- `collectionName`: string [REQUIRED] — Collection display name
- `dimension`: integer [REQUIRED for create] — Dimension value
- `data`: array [REQUIRED for insert] (vector objects) — Request payload data
- `vectors`: array [REQUIRED for search] (query vectors) — List of vectors
- `topK`: integer [OPTIONAL for search] — Topk value
- `filter`: string [OPTIONAL] (boolean expression) — Filter criteria

## Example Request Bodies

**Create a Collection:**
```json
{
  "collectionName": "product_embeddings",
  "dimension": 768
}
```

**Insert Vectors:**
```json
{
  "collectionName": "product_embeddings",
  "data": [
    {"id": 1, "vector": [0.1, 0.2, 0.3], "product_name": "Widget A"},
    {"id": 2, "vector": [0.4, 0.5, 0.6], "product_name": "Widget B"}
  ]
}
```

## Response

**Create object:**
- `id`: string — Unique create identifier
- `name`: string — Create name or title
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
