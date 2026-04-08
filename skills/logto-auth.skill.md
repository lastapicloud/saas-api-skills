---
name: logto-auth
description: Modern identity and authentication via Logto. Use when the user mentions logto, identity, IAM, authentication, OAuth, OIDC, SSO, user management.
version: 1.0.0
skill_type: external
base_url_env: LOGTO_BASE_URL
auth_env_var: LOGTO_API_KEY
auth_type: bearer
triggers:
  - logto
  - identity
  - IAM
  - authentication
  - OAuth
  - OIDC
  - SSO
  - user management
license: MIT
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://openapi.logto.io/
---

# Logto-Auth

Modern identity and authentication via Logto. Use when the user mentions logto, identity, IAM, authentication, OAuth, OIDC, SSO, user management.

## API Endpoints

- **GET** `/api/users` - List users
- **POST** `/api/users` - Create user
- **GET** `/api/users/{userId}` - Get user
- **PATCH** `/api/users/{userId}` - Update user
- **DELETE** `/api/users/{userId}` - Delete user
- **POST** `/api/users/{userId}/verify-password` - Verify user password
- **PATCH** `/api/users/{userId}/password` - Update user password
- **GET** `/api/users/{userId}/roles` - Get user roles
- **POST** `/api/users/{userId}/roles` - Assign roles to user
- **DELETE** `/api/users/{userId}/roles/{roleId}` - Remove role from user
- **GET** `/api/applications` - List applications
- **POST** `/api/applications` - Create application
- **GET** `/api/applications/{appId}` - Get application
- **PATCH** `/api/applications/{appId}` - Update application
- **DELETE** `/api/applications/{appId}` - Delete application
- **GET** `/api/roles` - List roles
- **POST** `/api/roles` - Create role
- **GET** `/api/roles/{roleId}` - Get role
- **PATCH** `/api/roles/{roleId}` - Update role
- **DELETE** `/api/roles/{roleId}` - Delete role
- **GET** `/api/resources` - List API resources
- **POST** `/api/resources` - Create API resource
- **GET** `/api/resources/{resourceId}` - Get resource
- **PATCH** `/api/resources/{resourceId}` - Update resource
- **DELETE** `/api/resources/{resourceId}` - Delete resource
- **GET** `/api/connectors` - List connectors
- **POST** `/api/connectors` - Create connector
- **GET** `/api/connectors/{connectorId}` - Get connector
- **PATCH** `/api/connectors/{connectorId}` - Update connector
- **DELETE** `/api/connectors/{connectorId}` - Delete connector
- **GET** `/api/hooks` - List hooks
- **POST** `/api/hooks` - Create hook
- **GET** `/api/hooks/{hookId}` - Get hook
- **PATCH** `/api/hooks/{hookId}` - Update hook
- **DELETE** `/api/hooks/{hookId}` - Delete hook
- **GET** `/api/organizations` - List organizations
- **POST** `/api/organizations` - Create organization
- **GET** `/api/organizations/{orgId}` - Get organization
- **PATCH** `/api/organizations/{orgId}` - Update organization
- **DELETE** `/api/organizations/{orgId}` - Delete organization

## Actions

- list_users: List users (GET /api/users)
- create_user: Create user (POST /api/users)
- get_user: Get user (GET /api/users/{userId})
- update_user: Update user (PATCH /api/users/{userId})
- delete_user: Delete user (DELETE /api/users/{userId})
- verify_password: Verify user password (POST /api/users/{userId}/verify-password)
- update_password: Update user password (PATCH /api/users/{userId}/password)
- list_applications: List applications (GET /api/applications)
- create_application: Create application (POST /api/applications)
- get_application: Get application (GET /api/applications/{appId})
- update_application: Update application (PATCH /api/applications/{appId})
- delete_application: Delete application (DELETE /api/applications/{appId})
- list_roles: List roles (GET /api/roles)
- create_role: Create role (POST /api/roles)
- get_role: Get role (GET /api/roles/{roleId})
- update_role: Update role (PATCH /api/roles/{roleId})
- delete_role: Delete role (DELETE /api/roles/{roleId})
- list_resources: List API resources (GET /api/resources)
- create_resource: Create API resource (POST /api/resources)
- get_resource: Get resource (GET /api/resources/{resourceId})
- update_resource: Update resource (PATCH /api/resources/{resourceId})
- delete_resource: Delete resource (DELETE /api/resources/{resourceId})
- list_connectors: List connectors (GET /api/connectors)
- create_connector: Create connector (POST /api/connectors)
- get_connector: Get connector (GET /api/connectors/{connectorId})
- update_connector: Update connector (PATCH /api/connectors/{connectorId})
- delete_connector: Delete connector (DELETE /api/connectors/{connectorId})
- list_hooks: List hooks (GET /api/hooks)
- create_hook: Create hook (POST /api/hooks)
- get_hook: Get hook (GET /api/hooks/{hookId})
- update_hook: Update hook (PATCH /api/hooks/{hookId})
- delete_hook: Delete hook (DELETE /api/hooks/{hookId})
- list_organizations: List organizations (GET /api/organizations)
- create_organization: Create organization (POST /api/organizations)
- get_organization: Get organization (GET /api/organizations/{orgId})
- update_organization: Update organization (PATCH /api/organizations/{orgId})
- delete_organization: Delete organization (DELETE /api/organizations/{orgId})

## Fields

- `email`: string [REQUIRED for create] - User email
- `name`: string [OPTIONAL] - User name
- `password`: string [REQUIRED for create] - User password
- `role_names`: array [OPTIONAL] - Role names to assign
- `app_type`: string [REQUIRED for create] - Application type (web, native, SPA, etc.)
- `name`: string [REQUIRED for create] - Resource/API name
- `indicator`: string [REQUIRED for create] - API indicator/identifier

## Example Request Bodies

**Create User:**
```json
{"email": "user@example.com", "name": "John Doe", "password": "securepassword123"}
```

**Create Application:**
```json
{"name": "My App", "app_type": "SPA", "oidc_client_id": "client-id", "oidc_client_secret": "client-secret"}
```

**Create Role:**
```json
{"name": "admin", "description": "Administrator role"}
```
