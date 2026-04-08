---
name: qdrant-vectors
description: Manage Qdrant vector collections and points. Use when the user mentions
  qdrant, vector, embedding, similarity, collection.
version: 1.0.0
skill_type: external
base_url_env: QDRANT_BASE_URL
auth_env_var: QDRANT_API_KEY
auth_type: header
triggers:
  - qdrant
  - vector
  - embedding
  - similarity
  - collection
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires QDRANT_BASE_URL and QDRANT_API_KEY environment variables.
---

# Qdrant-Vectors

Manage Qdrant vector collections and points. Use when the user mentions qdrant, vector, embedding, similarity, collection.

## API Endpoints

- **GET** `/collections` - List collections
- **GET** `/collections/{collection_name}` - Get collection info
- **PUT** `/collections/{collection_name}` - Create a collection
- **DELETE** `/collections/{collection_name}` - Delete a collection
- **PUT** `/collections/{collection_name}/points` - Upsert points
- **POST** `/collections/{collection_name}/points/search` - Search points
- **POST** `/collections/{collection_name}/points` - Get points by IDs
- **POST** `/collections/{collection_name}/points/delete` - Delete points
- **POST** `/collections/{collection_name}/points/scroll` - Scroll points
- **POST** `/collections/{collection_name}/points/recommend` - Recommend points

## Actions

- list: List collections (GET /collections)
- get_by_id: Get collection info (GET /collections/{collection_name})
- update: Create a collection (PUT /collections/{collection_name})
- delete: Delete a collection (DELETE /collections/{collection_name})
- put_points: Upsert points (PUT /collections/{collection_name}/points)
- search: Search points (POST /collections/{collection_name}/points/search)
- create: Get points by IDs (POST /collections/{collection_name}/points)
- create_delete: Delete points (POST /collections/{collection_name}/points/delete)
- create_scroll: Scroll points (POST /collections/{collection_name}/points/scroll)
- create_recommend: Recommend points (POST /collections/{collection_name}/points/recommend)

## Fields

- `vectors`: object [REQUIRED for create] with `size` (dimension), `distance` ("Cosine", "Euclid", "Dot")
- `points`: array [REQUIRED for upsert] with `id`, `vector`, `payload`
- `vector`: array [REQUIRED for search] (query vector)
- `limit`: integer [OPTIONAL for search]
- `filter`: object [OPTIONAL] (filter conditions)

## Example Request Bodies

**Create Collection:**
```json
{"vectors": {"size": 384, "distance": "Cosine"}}
```

**Search Points:**
```json
{"vector": [0.1, 0.2, 0.3, 0.4], "limit": 10, "filter": {"must": [{"key": "category", "match": {"value": "electronics"}}]}}
```
