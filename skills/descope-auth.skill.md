---
name: descope-auth
description: Manage users, tenants, and authentication via Descope. Use when the user
  mentions descope, auth, authentication, user, tenant, sso.
version: 1.0.0
skill_type: external
base_url_env: DESCOPE_BASE_URL
auth_env_var: DESCOPE_MANAGEMENT_KEY
auth_type: bearer
triggers:
  - descope
  - auth
  - authentication
  - user
  - tenant
  - sso
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires DESCOPE_BASE_URL and DESCOPE_MANAGEMENT_KEY environment variables.
---

# Descope-Auth

Manage users, tenants, and authentication via Descope. Use when the user mentions descope, auth, authentication, user, tenant, sso.

## API Endpoints

- **POST** `/v1/mgmt/user/create` - Create a user
- **POST** `/v1/mgmt/user/search` - Search users
- **POST** `/v1/mgmt/user/update` - Update a user
- **POST** `/v1/mgmt/user/delete` - Delete a user
- **POST** `/v1/mgmt/tenant/create` - Create a tenant
- **POST** `/v1/mgmt/tenant/search` - List tenants
- **POST** `/v1/mgmt/role/create` - Create a role
- **POST** `/v1/mgmt/role/search` - List roles

## Actions

- create: Create a user (POST /v1/mgmt/user/create)
- search: Search users (POST /v1/mgmt/user/search)
- create_update: Update a user (POST /v1/mgmt/user/update)
- create_delete: Delete a user (POST /v1/mgmt/user/delete)
- create_tenant: Create a tenant (POST /v1/mgmt/tenant/create)
- search_tenant: List tenants (POST /v1/mgmt/tenant/search)
- create_role: Create a role (POST /v1/mgmt/role/create)
- search_role: List roles (POST /v1/mgmt/role/search)

## Fields

- `loginId`: string [REQUIRED for create]
- `email`: string [OPTIONAL]
- `name`: string [OPTIONAL]
- `tenantIds`: array [OPTIONAL]

## Example Request Bodies

**Create User:**
```json
{"loginId": "user@example.com", "email": "user@example.com", "name": "Alex Thompson", "tenantIds": ["tenant-prod-01"]}
```

**Update User:**
```json
{"loginId": "user@example.com", "name": "Alex T. Thompson", "phone": "+1-555-987-6543"}
```
