---
name: fusionauth-identity
description: 'Manage FusionAuth users, applications, and groups. Use when the user
  mentions fusionauth, user, identity, authentication, application.

  '
version: 1.0.0
skill_type: external
base_url_env: FUSIONAUTH_BASE_URL
auth_env_var: FUSIONAUTH_API_KEY
auth_type: header
triggers:
  - fusionauth
  - user
  - identity
  - authentication
  - application
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FUSIONAUTH_BASE_URL and FUSIONAUTH_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Fusionauth-Identity

Manage FusionAuth users, applications, and groups. Use when the user mentions fusionauth, user, identity, authentication, application.


## API Endpoints

- **GET** `/api/user/search` - Search users
- **GET** `/api/user/{userId}` - Get a user
- **POST** `/api/user` - Create a user
- **PUT** `/api/user/{userId}` - Update a user
- **DELETE** `/api/user/{userId}` - Delete a user
- **GET** `/api/application` - List applications
- **POST** `/api/application` - Create an application
- **GET** `/api/group` - List groups
- **POST** `/api/group` - Create a group
- **GET** `/api/tenant` - List tenants

## Actions

- search: Search users (GET /api/user/search)
- get_by_id: Get a user (GET /api/user/{userId})
- create: Create a user (POST /api/user)
- update: Update a user (PUT /api/user/{userId})
- delete: Delete a user (DELETE /api/user/{userId})
- list: List applications (GET /api/application)
- create_application: Create an application (POST /api/application)
- list_groups: List groups (GET /api/group)
- create_group: Create a group (POST /api/group)
- list_tenants: List tenants (GET /api/tenant)

## Fields

- `user`: object [REQUIRED for create] with `email`, `password` — User configuration
- `firstName`: string [OPTIONAL] — First display name
- `lastName`: string [OPTIONAL] — Last display name
- `username`: string [OPTIONAL] — Username
- `application`: object [REQUIRED for create app] with `name` — Application configuration
- `group`: object [REQUIRED for create group] with `name` — Group configuration

## Example Request Bodies

**Create User:**
```json
{"user": {"email": "newuser@example.com", "password": "SecurePass123!"}, "firstName": "Jane", "lastName": "Doe"}
```

**Create Application:**
```json
{"application": {"name": "My Web App"}}

## Response

**User object:**
- `id`: string — Unique user identifier
- `name`: string — User name or title
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
