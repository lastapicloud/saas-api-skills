---
name: okta-auth
description: Manage users, groups, and applications via Okta. Use when the user mentions
  okta, auth, authentication, user, group, application, sso, identity.
version: 1.0.0
skill_type: external
base_url_env: OKTA_BASE_URL
auth_env_var: OKTA_API_TOKEN
auth_type: header
triggers:
  - okta
  - auth
  - authentication
  - user
  - group
  - application
  - sso
  - identity
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires OKTA_BASE_URL and OKTA_API_TOKEN environment variables.
---

# Okta-Auth

Manage users, groups, and applications via Okta. Use when the user mentions okta, auth, authentication, user, group, application, sso, identity.

## API Endpoints

- **GET** `/api/v1/users` - List users
- **POST** `/api/v1/users` - Create user
- **GET** `/api/v1/users/{userId}` - Get user
- **PUT** `/api/v1/users/{userId}` - Update user
- **DELETE** `/api/v1/users/{userId}` - Deactivate user
- **GET** `/api/v1/groups` - List groups
- **POST** `/api/v1/groups` - Create group
- **GET** `/api/v1/apps` - List applications
- **DELETE** `/api/v1/users/{userId}/sessions` - Clear User Sessions
- **GET** `/api/v1/users/me` - Get Current User

## Actions

- list: List users (GET /api/v1/users)
- create: Create user (POST /api/v1/users)
- get_by_id: Get user (GET /api/v1/users/{userId})
- update: Update user (PUT /api/v1/users/{userId})
- delete: Deactivate user (DELETE /api/v1/users/{userId})
- list_groups: List groups (GET /api/v1/groups)
- create_groups: Create group (POST /api/v1/groups)
- list_apps: List applications (GET /api/v1/apps)
- delete_sessions: Clear User Sessions (DELETE /api/v1/users/{userId}/sessions)
- list_me: Get Current User (GET /api/v1/users/me)

## Fields

- `profile`: object [REQUIRED for create] (firstName, lastName, email, login)
- `credentials`: object [OPTIONAL]
- `groupIds`: array [OPTIONAL]

## Example Request Bodies

**Create User:**
```json
{"profile": {"firstName": "Jane", "lastName": "Doe", "email": "jane.doe@example.com", "login": "jane.doe@example.com"}, "credentials": {"password": {"value": "SecurePass123!"}}}
```

**Create Group:**
```json
{"profile": {"name": "Engineering", "description": "Engineering team members"}}
```
