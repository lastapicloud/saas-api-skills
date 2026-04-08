---
name: zilliz-vectors
description: Manage Zilliz Cloud (Milvus) collections and vectors. Use when the user
  mentions zilliz, milvus, vector, embedding, collection.
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
- create_describe: Describe a collection (POST /v2/vectordb/collections/describe)
- create_drop: Drop a collection (POST /v2/vectordb/collections/drop)
- create_insert: Insert vectors (POST /v2/vectordb/entities/insert)
- search: Search vectors (POST /v2/vectordb/entities/search)
- query: Query vectors (POST /v2/vectordb/entities/query)
- create_delete: Delete vectors (POST /v2/vectordb/entities/delete)
- create_get: Get vectors by ID (POST /v2/vectordb/entities/get)
- create_indexes: Create an index (POST /v2/vectordb/indexes/create)

## Fields

- `collectionName`: string [REQUIRED]
- `dimension`: integer [REQUIRED for create]
- `data`: array [REQUIRED for insert] (vector objects)
- `vectors`: array [REQUIRED for search] (query vectors)
- `topK`: integer [OPTIONAL for search]
- `filter`: string [OPTIONAL] (boolean expression)

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
