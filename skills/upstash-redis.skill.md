---
name: upstash-redis
description: Manage Redis databases via Upstash. Use when the user mentions upstash,
  redis, serverless redis, cache, key-value.
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
- create_stats: Get stats (POST /v2/redis/database/{id}/stats)
- put_rename: Rename database (PUT /v2/redis/database/{id}/rename)
- create_reset_password: Reset password (POST /v2/redis/database/{id}/reset-password)

## Fields

- `name`: string [REQUIRED for create]
- `region`: string [REQUIRED for create]
- `tls`: boolean [OPTIONAL]

## Example Request Bodies

**Create Database:**
```json
{"name": "session-store", "region": "us-east-1", "tls": true}
```

**Rename Database:**
```json
{"name": "session-store-prod"}
```
