---
name: fusionauth-identity
description: Manage FusionAuth users, applications, and groups. Use when the user
  mentions fusionauth, user, identity, authentication, application.
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
- list_group: List groups (GET /api/group)
- create_group: Create a group (POST /api/group)
- list_tenant: List tenants (GET /api/tenant)

## Fields

- `user`: object [REQUIRED for create] with `email`, `password`
- `firstName`: string [OPTIONAL]
- `lastName`: string [OPTIONAL]
- `username`: string [OPTIONAL]
- `application`: object [REQUIRED for create app] with `name`
- `group`: object [REQUIRED for create group] with `name`

## Example Request Bodies

**Create User:**
```json
{"user": {"email": "newuser@example.com", "password": "SecurePass123!"}, "firstName": "Jane", "lastName": "Doe"}
```

**Create Application:**
```json
{"application": {"name": "My Web App"}}
