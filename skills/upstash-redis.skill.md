---
name: upstash-redis
description: 'Manage Redis databases via Upstash. Use when the user mentions upstash,
  redis, serverless redis, cache, key-value.

  '
version: 1.0.0
skill_type: external
base_url_env: UPSTASH_BASE_URL
auth_env_var: UPSTASH_API_KEY
auth_user_env: UPSTASH_EMAIL
auth_type: bearer
triggers:
  - upstash
  - redis
  - serverless redis
  - cache
  - key-value
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires UPSTASH_BASE_URL and UPSTASH_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Upstash-Redis

Manage Redis databases via Upstash. Use when the user mentions upstash, redis, serverless redis, cache, key-value.


## API Endpoints

- **GET** `/v2/redis/databases` - List databases
- **POST** `/v2/redis/database` - Create database
- **GET** `/v2/redis/database/{id}` - Get database
- **DELETE** `/v2/redis/database/{id}` - Delete database
- **POST** `/v2/redis/database/{id}/stats` - Get stats
- **PUT** `/v2/redis/database/{id}/rename` - Rename database
- **POST** `/v2/redis/database/{id}/reset-password` - Reset password

## Actions

- list: List databases (GET /v2/redis/databases)
- create: Create database (POST /v2/redis/database)
- get_by_id: Get database (GET /v2/redis/database/{id})
- delete: Delete database (DELETE /v2/redis/database/{id})
- get_stats: Get stats (POST /v2/redis/database/{id}/stats)
- put_rename: Rename database (PUT /v2/redis/database/{id}/rename)
- create_reset_password: Reset password (POST /v2/redis/database/{id}/reset-password)

## Fields

- `name`: string [REQUIRED for create] — Display name
- `region`: string [REQUIRED for create] — Region
- `tls`: boolean [OPTIONAL] — Whether tls is enabled

## Example Request Bodies

**Create Database:**
```json
{"name": "session-store", "region": "us-east-1", "tls": true}
```

**Rename Database:**
```json
{"name": "session-store-prod"}
```

## Response

**Database object:**
- `id`: string — Unique database identifier
- `name`: string — Database name or title
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
