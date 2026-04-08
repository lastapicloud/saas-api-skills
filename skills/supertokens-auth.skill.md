---
name: supertokens-auth
description: Manage users and sessions via SuperTokens. Use when the user mentions
  supertokens, auth, authentication, user, session, recipe.
version: 1.0.0
skill_type: external
base_url_env: SUPERTOKENS_BASE_URL
auth_env_var: SUPERTOKENS_API_KEY
auth_type: header
triggers:
  - supertokens
  - auth
  - authentication
  - user
  - session
  - recipe
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SUPERTOKENS_BASE_URL and SUPERTOKENS_API_KEY environment variables.
---

# Supertokens-Auth

Manage users and sessions via SuperTokens. Use when the user mentions supertokens, auth, authentication, user, session, recipe.

## API Endpoints

- **GET** `/recipe/users` - List users
- **GET** `/recipe/user` - Get user by ID
- **DELETE** `/recipe/user` - Delete user
- **PUT** `/recipe/user/metadata` - Update user metadata
- **GET** `/recipe/user/metadata` - Get user metadata
- **GET** `/recipe/session/user` - Get user sessions
- **POST** `/recipe/session/remove` - Revoke sessions
- **GET** `/recipe/dashboard/users/count` - Get user count

## Actions

- list: List users (GET /recipe/users)
- list_user: Get user by ID (GET /recipe/user)
- delete_user: Delete user (DELETE /recipe/user)
- put_metadata: Update user metadata (PUT /recipe/user/metadata)
- list_metadata: Get user metadata (GET /recipe/user/metadata)
- list_user_2: Get user sessions (GET /recipe/session/user)
- create: Revoke sessions (POST /recipe/session/remove)
- list_count: Get user count (GET /recipe/dashboard/users/count)

## Fields

- `userId`: string [REQUIRED]
- `email`: string [OPTIONAL]
- `metadata`: object [OPTIONAL]

## Example Request Bodies

**Update User Metadata:**
```json
{"userId": "abc123-def456", "metadata": {"role": "admin", "plan": "enterprise"}}
```

**Revoke Sessions:**
```json
{"userId": "abc123-def456"}
```
