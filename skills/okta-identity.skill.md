---
name: okta-identity
description: Manage Okta users, groups, and applications. Use when the user mentions
  okta, user, identity, SSO, group, application.
version: 1.0.0
skill_type: external
base_url_env: OKTA_BASE_URL
auth_env_var: OKTA_API_TOKEN
auth_type: header
triggers:
  - okta
  - user
  - identity
  - SSO
  - group
  - application
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires OKTA_BASE_URL and OKTA_API_TOKEN environment variables.
---

# Okta-Identity

Manage Okta users, groups, and applications. Use when the user mentions okta, user, identity, SSO, group, application.

## API Endpoints

- **GET** `/api/v1/users` - List users
- **GET** `/api/v1/users/{userId}` - Get a user
- **POST** `/api/v1/users` - Create a user
- **PUT** `/api/v1/users/{userId}` - Update a user
- **DELETE** `/api/v1/users/{userId}` - Deactivate a user
- **GET** `/api/v1/groups` - List groups
- **POST** `/api/v1/groups` - Create a group
- **GET** `/api/v1/apps` - List applications
- **POST** `/api/v1/users/{userId}/lifecycle/activate` - Activate a user
- **POST** `/api/v1/users/{userId}/lifecycle/suspend` - Suspend a user
- **DELETE** `/api/v1/users/{userId}/sessions` - Clear User Sessions
- **GET** `/api/v1/users/me` - Get Current User

## Actions

- list: List users (GET /api/v1/users)
- get_by_id: Get a user (GET /api/v1/users/{userId})
- create: Create a user (POST /api/v1/users)
- update: Update a user (PUT /api/v1/users/{userId})
- delete: Deactivate a user (DELETE /api/v1/users/{userId})
- list_groups: List groups (GET /api/v1/groups)
- create_groups: Create a group (POST /api/v1/groups)
- list_apps: List applications (GET /api/v1/apps)
- create_activate: Activate a user (POST /api/v1/users/{userId}/lifecycle/activate)
- create_suspend: Suspend a user (POST /api/v1/users/{userId}/lifecycle/suspend)
- delete_sessions: Clear User Sessions (DELETE /api/v1/users/{userId}/sessions)
- list_me: Get Current User (GET /api/v1/users/me)

## Fields

- `profile`: object [REQUIRED for create] with `firstName`, `lastName`, `email`, `login`
- `credentials`: object [OPTIONAL] with `password.value`
- `groupProfile`: object [REQUIRED for create group] with `name`, `description`

## Example Request Bodies

**Create User:**
```json
{"profile": {"firstName": "Alex", "lastName": "Smith", "email": "alex.smith@example.com", "login": "alex.smith@example.com"}, "credentials": {"password": {"value": "TempPass456!"}}}
```

**Create Group:**
```json
{"profile": {"name": "DevOps Team", "description": "Members of the DevOps team"}}
```
