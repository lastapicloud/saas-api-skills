---
name: weaviate-vectors
description: Manage Weaviate vector collections and objects. Use when the user mentions
  weaviate, vector, embedding, similarity, collection, object.
version: 1.0.0
skill_type: external
base_url_env: WEAVIATE_BASE_URL
auth_env_var: WEAVIATE_API_KEY
auth_type: header
triggers:
  - weaviate
  - vector
  - embedding
  - similarity
  - collection
  - object
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires WEAVIATE_BASE_URL and WEAVIATE_API_KEY environment variables.
---

# Weaviate-Vectors

Manage Weaviate vector collections and objects. Use when the user mentions weaviate, vector, embedding, similarity, collection, object.

## API Endpoints

- **GET** `/v1/schema` - List classes (collections)
- **POST** `/v1/schema` - Create a class
- **DELETE** `/v1/schema/{className}` - Delete a class
- **POST** `/v1/objects` - Create an object
- **GET** `/v1/objects/{className}/{id}` - Get an object
- **PATCH** `/v1/objects/{className}/{id}` - Update an object
- **DELETE** `/v1/objects/{className}/{id}` - Delete an object
- **POST** `/v1/graphql` - GraphQL query (search/filter)
- **GET** `/v1/objects` - List objects
- **POST** `/v1/batch/objects` - Batch create objects

## Actions

- list: List classes (collections) (GET /v1/schema)
- create: Create a class (POST /v1/schema)
- delete: Delete a class (DELETE /v1/schema/{className})
- create_objects: Create an object (POST /v1/objects)
- get_by_id: Get an object (GET /v1/objects/{className}/{id})
- update: Update an object (PATCH /v1/objects/{className}/{id})
- delete_objects: Delete an object (DELETE /v1/objects/{className}/{id})
- create_graphql: GraphQL query (search/filter) (POST /v1/graphql)
- list_objects: List objects (GET /v1/objects)
- create_objects_2: Batch create objects (POST /v1/batch/objects)

## Fields

- `class`: string [REQUIRED for create class/object]
- `properties`: object [REQUIRED for create object]
- `vector`: array [OPTIONAL] (manual vector)
- `query`: string [REQUIRED for GraphQL search]

## Example Request Bodies

**Create Object:**
```json
{"class": "Article", "properties": {"title": "Introduction to Vector Databases", "content": "Vector databases store data as high-dimensional vectors..."}}
```

**Update Object:**
```json
{"properties": {"title": "Updated: Introduction to Vector Databases"}}
