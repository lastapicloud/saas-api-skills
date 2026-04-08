---
name: frontegg-auth
description: Customer identity and access management via Frontegg. Use when the user mentions frontegg, CIAM, customer auth, identity management, user management.
version: 1.0.0
skill_type: external
base_url_env: FRONTEGG_BASE_URL
auth_env_var: FRONTEGG_API_KEY
auth_type: bearer
triggers:
  - frontegg
  - CIAM
  - customer auth
  - identity management
  - user management
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://developers.frontegg.com/
---

# Frontegg-Auth

Customer identity and access management via Frontegg. Use when the user mentions frontegg, CIAM, customer auth, identity management, user management.

## API Endpoints

- **POST** `/identity/resources/auth/v1` - Authenticate user with password
- **POST** `/identity/resources/users/v1` - Create user
- **GET** `/identity/resources/users/v1` - List users
- **GET** `/identity/resources/users/v1/{userId}` - Get user by ID
- **PUT** `/identity/resources/users/v1/{userId}` - Update user
- **DELETE** `/identity/resources/users/v1/{userId}` - Delete user
- **POST** `/identity/resources/users/v1/{userId}/verify-email` - Verify user email
- **POST** `/identity/resources/users/v1/{userId}/reset-password` - Reset user password
- **POST** `/identity/resources/users/v1/{userId}/send-verification-email` - Send verification email
- **GET** `/identity/resources/roles/v1` - List roles
- **POST** `/identity/resources/roles/v1` - Create role
- **PUT** `/identity/resources/roles/v1/{roleId}` - Update role
- **DELETE** `/identity/resources/roles/v1/{roleId}` - Delete role
- **GET** `/identity/resources/permissions/v1` - List permissions
- **POST** `/identity/resources/permissions/v1` - Create permission
- **GET** `/identity/resources/api-keys/v1` - List API keys
- **POST** `/identity/resources/api-keys/v1` - Create API key
- **DELETE** `/identity/resources/api-keys/v1/{keyId}` - Delete API key
- **GET** `/identity/resources/webhooks/v1` - List webhooks
- **POST** `/identity/resources/webhooks/v1` - Create webhook
- **PUT** `/identity/resources/webhooks/v1/{webhookId}` - Update webhook
- **DELETE** `/identity/resources/webhooks/v1/{webhookId}` - Delete webhook
- **POST** `/identity/resources/webhooks/v1/{webhookId}/test` - Test webhook

## Actions

- authenticate: Authenticate user with password (POST /identity/resources/auth/v1)
- create_user: Create user (POST /identity/resources/users/v1)
- list_users: List users (GET /identity/resources/users/v1)
- get_user: Get user by ID (GET /identity/resources/users/v1/{userId})
- update_user: Update user (PUT /identity/resources/users/v1/{userId})
- delete_user: Delete user (DELETE /identity/resources/users/v1/{userId})
- verify_email: Verify user email (POST /identity/resources/users/v1/{userId}/verify-email)
- reset_password: Reset user password (POST /identity/resources/users/v1/{userId}/reset-password)
- send_verification: Send verification email (POST /identity/resources/users/v1/{userId}/send-verification-email)
- list_roles: List roles (GET /identity/resources/roles/v1)
- create_role: Create role (POST /identity/resources/roles/v1)
- update_role: Update role (PUT /identity/resources/roles/v1/{roleId})
- delete_role: Delete role (DELETE /identity/resources/roles/v1/{roleId})
- list_permissions: List permissions (GET /identity/resources/permissions/v1)
- create_permission: Create permission (POST /identity/resources/permissions/v1)
- list_api_keys: List API keys (GET /identity/resources/api-keys/v1)
- create_api_key: Create API key (POST /identity/resources/api-keys/v1)
- delete_api_key: Delete API key (DELETE /identity/resources/api-keys/v1/{keyId})
- list_webhooks: List webhooks (GET /identity/resources/webhooks/v1)
- create_webhook: Create webhook (POST /identity/resources/webhooks/v1)
- update_webhook: Update webhook (PUT /identity/resources/webhooks/v1/{webhookId})
- delete_webhook: Delete webhook (DELETE /identity/resources/webhooks/v1/{webhookId})
- test_webhook: Test webhook (POST /identity/resources/webhooks/v1/{webhookId}/test)

## Fields

- `email`: string [REQUIRED for create] - User email
- `name`: string [OPTIONAL] - User name
- `password`: string [REQUIRED for create] - User password
- `role_id`: string [OPTIONAL] - Role ID to assign
- `permissions`: array [OPTIONAL] - List of permissions

## Example Request Bodies

**Authenticate User:**
```json
{"email": "user@example.com", "password": "securepassword123"}
```

**Create User:**
```json
{"email": "user@example.com", "name": "John Doe", "password": "securepassword123"}
```

**Create Role:**
```json
{"name": "Admin", "permissions": ["read", "write", "delete"]}
```
