---
name: stytch-auth
description: Manage users and sessions via Stytch. Use when the user mentions stytch,
  auth, authentication, user, session, otp, magic link.
version: 1.0.0
skill_type: external
base_url_env: STYTCH_BASE_URL
auth_env_var: STYTCH_SECRET
auth_user_env: STYTCH_PROJECT_ID
auth_type: basic
triggers:
  - stytch
  - auth
  - authentication
  - user
  - session
  - otp
  - magic link
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires STYTCH_BASE_URL and STYTCH_SECRET environment variables.
---

# Stytch-Auth

Manage users and sessions via Stytch. Use when the user mentions stytch, auth, authentication, user, session, otp, magic link.

## API Endpoints

- **POST** `/v1/users` - Create user
- **GET** `/v1/users/{user_id}` - Get user
- **PUT** `/v1/users/{user_id}` - Update user
- **DELETE** `/v1/users/{user_id}` - Delete user
- **POST** `/v1/users/search` - Search users
- **POST** `/v1/magic_links/email/send` - Send magic link
- **POST** `/v1/otps/email/send` - Send email OTP
- **POST** `/v1/sessions/authenticate` - Authenticate session

## Actions

- create: Create user (POST /v1/users)
- get_by_id: Get user (GET /v1/users/{user_id})
- update: Update user (PUT /v1/users/{user_id})
- delete: Delete user (DELETE /v1/users/{user_id})
- search: Search users (POST /v1/users/search)
- create_send: Send magic link (POST /v1/magic_links/email/send)
- create_send_2: Send email OTP (POST /v1/otps/email/send)
- create_authenticate: Authenticate session (POST /v1/sessions/authenticate)

## Fields

- `email`: string [REQUIRED for create]
- `name`: object [OPTIONAL] (first_name, last_name)

## Example Request Bodies

**Create User:**
```json
{"email": "user@example.com", "name": {"first_name": "Jane", "last_name": "Doe"}}
```

**Send Magic Link:**
```json
{"email": "user@example.com"}
```
