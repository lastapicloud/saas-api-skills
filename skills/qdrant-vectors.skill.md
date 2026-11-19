---
name: qdrant-vectors
description: 'Manage Qdrant vector collections and points. Use when the user mentions
  qdrant, vector, embedding, similarity, collection.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
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
- delete_points: Delete points (POST /collections/{collection_name}/points/delete)
- create_scroll_points: Scroll points (POST /collections/{collection_name}/points/scroll)
- create_recommend_points: Recommend points (POST /collections/{collection_name}/points/recommend)

## Fields

- `vectors`: object [REQUIRED for create] with `size` (dimension), `distance` ("Cosine", "Euclid", "Dot") — Vectors configuration
- `points`: array [REQUIRED for upsert] with `id`, `vector`, `payload` — List of points
- `vector`: array [REQUIRED for search] (query vector) — List of vector
- `limit`: integer [OPTIONAL for search] — Maximum number of results
- `filter`: object [OPTIONAL] (filter conditions) — Filter criteria

## Example Request Bodies

**Create Collection:**
```json
{"vectors": {"size": 384, "distance": "Cosine"}}
```

**Search Points:**
```json
{"vector": [0.1, 0.2, 0.3, 0.4], "limit": 10, "filter": {"must": [{"key": "category", "match": {"value": "electronics"}}]}}
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
