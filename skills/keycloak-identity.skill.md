---
name: keycloak-identity
description: Manage Keycloak users, roles, and realms. Use when the user mentions
  keycloak, user, identity, realm, role, SSO.
version: 1.0.0
skill_type: external
base_url_env: KEYCLOAK_BASE_URL
auth_env_var: KEYCLOAK_ACCESS_TOKEN
auth_type: bearer
triggers:
  - keycloak
  - user
  - identity
  - realm
  - role
  - SSO
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires KEYCLOAK_BASE_URL and KEYCLOAK_ACCESS_TOKEN environment variables.
---

# Keycloak-Identity

Manage Keycloak users, roles, and realms. Use when the user mentions keycloak, user, identity, realm, role, SSO.

## API Endpoints

- **GET** `/admin/realms/{realm}/users` - List users
- **GET** `/admin/realms/{realm}/users/{userId}` - Get a user
- **POST** `/admin/realms/{realm}/users` - Create a user
- **PUT** `/admin/realms/{realm}/users/{userId}` - Update a user
- **DELETE** `/admin/realms/{realm}/users/{userId}` - Delete a user
- **GET** `/admin/realms/{realm}/roles` - List roles
- **POST** `/admin/realms/{realm}/roles` - Create a role
- **GET** `/admin/realms/{realm}/groups` - List groups
- **GET** `/admin/realms/{realm}/clients` - List clients
- **GET** `/admin/realms` - List realms
- **GET** `/{realm}/roles` - Get all roles for the realm or client
- **PUT** `/{realm}/roles/{role-name}` - Update a role by name
- **DELETE** `/{realm}/roles/{role-name}` - Delete a role by name
- **POST** `/{realm}/roles` - Create a new role for the realm or client
- **GET** `/{realm}/roles-by-id/{role-id}` - Get a specific role’s representation

## Actions

- list: List users (GET /admin/realms/{realm}/users)
- get_by_id: Get a user (GET /admin/realms/{realm}/users/{userId})
- create: Create a user (POST /admin/realms/{realm}/users)
- update: Update a user (PUT /admin/realms/{realm}/users/{userId})
- delete: Delete a user (DELETE /admin/realms/{realm}/users/{userId})
- list_roles: List roles (GET /admin/realms/{realm}/roles)
- create_roles: Create a role (POST /admin/realms/{realm}/roles)
- list_groups: List groups (GET /admin/realms/{realm}/groups)
- list_clients: List clients (GET /admin/realms/{realm}/clients)
- list_realms: List realms (GET /admin/realms)
- list_roles_2: Get all roles for the realm or client (GET /{realm}/roles)
- update_roles: Update a role by name (PUT /{realm}/roles/{role-name})
- delete_roles: Delete a role by name (DELETE /{realm}/roles/{role-name})
- create_roles_2: Create a new role for the realm or client (POST /{realm}/roles)
- get_by_id_roles_by_id: Get a specific role’s representation (GET /{realm}/roles-by-id/{role-id})

## Fields

- `username`: string [REQUIRED for create]
- `email`: string [OPTIONAL]
- `firstName`: string [OPTIONAL]
- `lastName`: string [OPTIONAL]
- `enabled`: boolean [REQUIRED for create]
- `credentials`: array [OPTIONAL] with `type`, `value`, `temporary`

## Example Request Bodies

**Create User:**
```json
{"username": "jdoe", "email": "jdoe@example.com", "firstName": "John", "lastName": "Doe", "enabled": true, "credentials": [{"type": "password", "value": "SecurePass123!", "temporary": false}]}
```

**Create Role:**
```json
{"name": "app-admin", "description": "Application administrator role"}
```
