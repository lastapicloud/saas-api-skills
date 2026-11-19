---
name: linkedin-social
description: 'Manage LinkedIn posts, profile, and connections. Use when the user mentions
  linkedin, post, profile, connection, social.

  '
version: 1.0.0
skill_type: external
base_url_env: LINKEDIN_BASE_URL
auth_env_var: LINKEDIN_ACCESS_TOKEN
auth_type: bearer
triggers:
  - linkedin
  - post
  - profile
  - connection
  - social
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires LINKEDIN_BASE_URL and LINKEDIN_ACCESS_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Linkedin-Social

Manage LinkedIn posts, profile, and connections. Use when the user mentions linkedin, post, profile, connection, social.


## API Endpoints

- **GET** `/v2/userinfo` - Get current user info
- **POST** `/v2/ugcPosts` - Create a post
- **GET** `/v2/ugcPosts/{postId}` - Get a post
- **DELETE** `/v2/ugcPosts/{postId}` - Delete a post
- **GET** `/v2/connections` - List connections
- **GET** `/v2/{id}` - Get share statistics
- **POST** `/v2/shares` - Share content
- **GET** `/v2/me` - Get profile

## Actions

- list: Get current user info (GET /v2/userinfo)
- create: Create a post (POST /v2/ugcPosts)
- get_by_id: Get a post (GET /v2/ugcPosts/{postId})
- delete: Delete a post (DELETE /v2/ugcPosts/{postId})
- list_connections: List connections (GET /v2/connections)
- get_share_statistics: Get share statistics (GET /v2/{id})
- create_share_content: Share content (POST /v2/shares)
- get_profile: Get profile (GET /v2/me)

## Fields

- `author`: string [REQUIRED for post] (e.g., "urn:li:person:{personId}") — Author
- `lifecycleState`: string [REQUIRED] ("PUBLISHED") — Lifecycle state or region
- `specificContent`: object [REQUIRED] with `shareCommentary`, `shareMediaCategory` — Specific content body
- `visibility`: object [REQUIRED] with `memberNetworkVisibility` ("PUBLIC") — Visibility configuration

## Example Request Bodies

**Create Post:**
```json
{"author": "urn:li:person:abc123", "lifecycleState": "PUBLISHED", "specificContent": {"shareCommentary": {"text": "Excited to share our latest update!"}, "shareMediaCategory": "NONE"}, "visibility": {"memberNetworkVisibility": "PUBLIC"}}
```

**Share Content:**
```json
{"author": "urn:li:person:abc123", "specificContent": {"shareCommentary": {"text": "Check out this article"}, "shareMediaCategory": "ARTICLE"}, "visibility": {"memberNetworkVisibility": "PUBLIC"}}
```

## Response

**Ugcpost object:**
- `id`: string — Unique ugcpost identifier
- `name`: string — Ugcpost name or title
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
