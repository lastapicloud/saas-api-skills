---
name: workos-identity
description: Manage WorkOS users, organizations, and SSO connections. Use when the
  user mentions workos, user, organization, SSO, directory.
version: 1.0.0
skill_type: external
base_url_env: WORKOS_BASE_URL
auth_env_var: WORKOS_API_KEY
auth_type: bearer
triggers:
  - workos
  - user
  - organization
  - SSO
  - directory
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires WORKOS_BASE_URL and WORKOS_API_KEY environment variables.
---

# Workos-Identity

Manage WorkOS users, organizations, and SSO connections. Use when the user mentions workos, user, organization, SSO, directory.

## API Endpoints

- **GET** `/user_management/users` - List users
- **GET** `/user_management/users/{userId}` - Get a user
- **POST** `/user_management/users` - Create a user
- **PUT** `/user_management/users/{userId}` - Update a user
- **DELETE** `/user_management/users/{userId}` - Delete a user
- **GET** `/organizations` - List organizations
- **POST** `/organizations` - Create an organization
- **GET** `/directory_sync/directories` - List directories
- **GET** `/sso/connections` - List SSO connections
- **GET** `/events` - List events

## Actions

- list: List users (GET /user_management/users)
- get_by_id: Get a user (GET /user_management/users/{userId})
- create: Create a user (POST /user_management/users)
- update: Update a user (PUT /user_management/users/{userId})
- delete: Delete a user (DELETE /user_management/users/{userId})
- list_organizations: List organizations (GET /organizations)
- create_organizations: Create an organization (POST /organizations)
- list_directories: List directories (GET /directory_sync/directories)
- list_connections: List SSO connections (GET /sso/connections)
- list_events: List events (GET /events)

## Fields

- `email`: string [REQUIRED for create user]
- `first_name`: string [OPTIONAL]
- `last_name`: string [OPTIONAL]
- `name`: string [REQUIRED for create organization]
- `domains`: array of strings [OPTIONAL for organization]

## Example Request Bodies

**Create User:**
```json
{"email": "jane@example.com", "first_name": "Jane", "last_name": "Doe"}
```

**Create Organization:**
```json
{"name": "Acme Corp", "domains": ["acme.com"]}
```
