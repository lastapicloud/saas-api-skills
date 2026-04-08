---
name: microsoft-entra-id
description: Manage users and groups via Microsoft Entra ID. Use when the user mentions
  microsoft entra id, entra, azure ad, active directory, user, group, identity.
version: 1.0.0
skill_type: external
base_url_env: MICROSOFT_ENTRA_ID_BASE_URL
auth_env_var: MICROSOFT_ENTRA_ID_ACCESS_TOKEN
auth_type: bearer
triggers:
  - microsoft entra id
  - entra
  - azure ad
  - active directory
  - user
  - group
  - identity
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MICROSOFT_ENTRA_ID_BASE_URL and MICROSOFT_ENTRA_ID_ACCESS_TOKEN
  environment variables.
---

# Microsoft-Entra-Id

Manage users and groups via Microsoft Entra ID. Use when the user mentions microsoft entra id, entra, azure ad, active directory, user, group, identity.

## API Endpoints

- **GET** `/v1.0/users` - List users
- **POST** `/v1.0/users` - Create user
- **GET** `/v1.0/users/{id}` - Get user
- **PATCH** `/v1.0/users/{id}` - Update user
- **DELETE** `/v1.0/users/{id}` - Delete user
- **GET** `/v1.0/groups` - List groups
- **POST** `/v1.0/groups` - Create group
- **GET** `/v1.0/applications` - List applications

## Actions

- list: List users (GET /v1.0/users)
- create: Create user (POST /v1.0/users)
- get_by_id: Get user (GET /v1.0/users/{id})
- update: Update user (PATCH /v1.0/users/{id})
- delete: Delete user (DELETE /v1.0/users/{id})
- list_groups: List groups (GET /v1.0/groups)
- create_groups: Create group (POST /v1.0/groups)
- list_applications: List applications (GET /v1.0/applications)

## Fields

- `displayName`: string [REQUIRED for create]
- `mailNickname`: string [REQUIRED for create]
- `userPrincipalName`: string [REQUIRED for create]
- `accountEnabled`: boolean [REQUIRED for create]
- `passwordProfile`: object [REQUIRED for create]

## Example Request Bodies

**Create User:**
```json
{"displayName": "Jane Smith", "mailNickname": "jsmith", "userPrincipalName": "jsmith@contoso.onmicrosoft.com", "accountEnabled": true, "passwordProfile": {"password": "SecurePass123!", "forceChangePasswordNextSignIn": true}}
```

**Create Group:**
```json
{"displayName": "Engineering Team", "mailEnabled": false, "mailNickname": "engineering", "securityEnabled": true}
```
