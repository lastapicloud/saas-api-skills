---
name: kinde-auth
description: Manage users and organizations via Kinde. Use when the user mentions
  kinde, auth, authentication, user, organization, identity.
version: 1.0.0
skill_type: external
base_url_env: KINDE_BASE_URL
auth_env_var: KINDE_MANAGEMENT_API_TOKEN
auth_type: bearer
triggers:
  - kinde
  - auth
  - authentication
  - user
  - organization
  - identity
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires KINDE_BASE_URL and KINDE_MANAGEMENT_API_TOKEN environment
  variables.
---

# Kinde-Auth

Manage users and organizations via Kinde. Use when the user mentions kinde, auth, authentication, user, organization, identity.

## API Endpoints

- **GET** `/api/v1/users` - List users
- **POST** `/api/v1/user` - Create user
- **GET** `/api/v1/user` - Get user
- **PATCH** `/api/v1/user` - Update user
- **DELETE** `/api/v1/user` - Delete user
- **GET** `/api/v1/organizations` - List organizations
- **POST** `/api/v1/organization` - Create organization
- **GET** `/api/v1/roles` - List roles

## Actions

- list: List users (GET /api/v1/users)
- create: Create user (POST /api/v1/user)
- list_user: Get user (GET /api/v1/user)
- patch_user: Update user (PATCH /api/v1/user)
- delete_user: Delete user (DELETE /api/v1/user)
- list_organizations: List organizations (GET /api/v1/organizations)
- create_organization: Create organization (POST /api/v1/organization)
- list_roles: List roles (GET /api/v1/roles)

## Fields

- `given_name`: string [OPTIONAL]
- `family_name`: string [OPTIONAL]
- `email`: string [REQUIRED for create]

## Example Request Bodies

**Create User:**
```json
{"given_name": "Alice", "family_name": "Smith", "email": "alice.smith@example.com"}
```

**Create Organization:**
```json
{"name": "Acme Corp", "handle": "acme-corp"}
```
