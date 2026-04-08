---
name: linkedin-social
description: Manage LinkedIn posts, profile, and connections. Use when the user mentions
  linkedin, post, profile, connection, social.
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
---

# Linkedin-Social

Manage LinkedIn posts, profile, and connections. Use when the user mentions linkedin, post, profile, connection, social.

## API Endpoints

- **GET** `/v2/userinfo` - Get current user info
- **POST** `/v2/ugcPosts` - Create a post
- **GET** `/v2/ugcPosts/{postId}` - Get a post
- **DELETE** `/v2/ugcPosts/{postId}` - Delete a post
- **GET** `/v2/connections` - List connections
- **GET** `/v2/organizationalEntityShareStatistics` - Get share statistics
- **POST** `/v2/shares` - Share content
- **GET** `/v2/me` - Get profile

## Actions

- list: Get current user info (GET /v2/userinfo)
- create: Create a post (POST /v2/ugcPosts)
- get_by_id: Get a post (GET /v2/ugcPosts/{postId})
- delete: Delete a post (DELETE /v2/ugcPosts/{postId})
- list_connections: List connections (GET /v2/connections)
- list_organizationalentitysharestatistics: Get share statistics (GET /v2/organizationalEntityShareStatistics)
- create_shares: Share content (POST /v2/shares)
- list_me: Get profile (GET /v2/me)

## Fields

- `author`: string [REQUIRED for post] (e.g., "urn:li:person:{personId}")
- `lifecycleState`: string [REQUIRED] ("PUBLISHED")
- `specificContent`: object [REQUIRED] with `shareCommentary`, `shareMediaCategory`
- `visibility`: object [REQUIRED] with `memberNetworkVisibility` ("PUBLIC")

## Example Request Bodies

**Create Post:**
```json
{"author": "urn:li:person:abc123", "lifecycleState": "PUBLISHED", "specificContent": {"shareCommentary": {"text": "Excited to share our latest update!"}, "shareMediaCategory": "NONE"}, "visibility": {"memberNetworkVisibility": "PUBLIC"}}
```

**Share Content:**
```json
{"author": "urn:li:person:abc123", "specificContent": {"shareCommentary": {"text": "Check out this article"}, "shareMediaCategory": "ARTICLE"}, "visibility": {"memberNetworkVisibility": "PUBLIC"}}
```
