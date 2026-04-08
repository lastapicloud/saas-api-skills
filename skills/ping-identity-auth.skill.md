---
name: ping-identity-auth
description: Manage users and groups via PingOne. Use when the user mentions ping
  identity, pingone, ping, auth, user, identity, sso.
version: 1.0.0
skill_type: external
base_url_env: PING_IDENTITY_BASE_URL
auth_env_var: PING_IDENTITY_ACCESS_TOKEN
auth_type: bearer
triggers:
  - ping identity
  - pingone
  - ping
  - auth
  - user
  - identity
  - sso
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PING_IDENTITY_BASE_URL and PING_IDENTITY_ACCESS_TOKEN environment
  variables.
---

# Ping-Identity-Auth

Manage users and groups via PingOne. Use when the user mentions ping identity, pingone, ping, auth, user, identity, sso.

## API Endpoints

- **GET** `/v1/environments/{envId}/users` - List users
- **POST** `/v1/environments/{envId}/users` - Create user
- **GET** `/v1/environments/{envId}/users/{userId}` - Get user
- **PUT** `/v1/environments/{envId}/users/{userId}` - Update user
- **DELETE** `/v1/environments/{envId}/users/{userId}` - Delete user
- **GET** `/v1/environments/{envId}/groups` - List groups
- **GET** `/v1/environments` - List environments

## Actions

- list: List users (GET /v1/environments/{envId}/users)
- create: Create user (POST /v1/environments/{envId}/users)
- get_by_id: Get user (GET /v1/environments/{envId}/users/{userId})
- update: Update user (PUT /v1/environments/{envId}/users/{userId})
- delete: Delete user (DELETE /v1/environments/{envId}/users/{userId})
- list_groups: List groups (GET /v1/environments/{envId}/groups)
- list_environments: List environments (GET /v1/environments)

## Fields

- `email`: string [REQUIRED for create]
- `username`: string [REQUIRED for create]
- `name`: object [OPTIONAL] (given, family)

## Example Request Bodies

**Create User:**
```json
{"email": "jdoe@example.com", "username": "jdoe", "name": {"given": "John", "family": "Doe"}}
```

**Update User:**
```json
{"email": "john.doe@example.com", "name": {"given": "John", "family": "Doe-Smith"}}
```
