---
name: hanko-auth
description: Passwordless authentication via Hanko. Use when the user mentions hanko, passwordless, passkey, WebAuthn, FIDO, user authentication.
version: 1.0.0
skill_type: external
base_url_env: HANKO_BASE_URL
auth_env_var: HANKO_API_KEY
auth_type: bearer
triggers:
  - hanko
  - passwordless
  - passkey
  - WebAuthn
  - FIDO
  - user authentication
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://docs.hanko.io/api-reference/introduction
---

# Hanko-Auth

Passwordless authentication via Hanko. Use when the user mentions hanko, passwordless, passkey, WebAuthn, FIDO, user authentication.

## API Endpoints

- **POST** `/v1/users` - Create user
- **GET** `/v1/users` - List users
- **GET** `/v1/users/{userId}` - Get user
- **DELETE** `/v1/users/{userId}` - Delete user
- **GET** `/v1/users/{userId}/credentials` - List user credentials
- **DELETE** `/v1/users/{userId}/credentials/{credentialId}` - Delete credential
- **POST** `/v1/relyingparties` - Create relying party
- **GET** `/v1/relyingparties` - List relying parties
- **GET** `/v1/relyingparties/{rpId}` - Get relying party
- **DELETE** `/v1/relyingparties/{rpId}` - Delete relying party
- **GET** `/v1/organizations` - List organizations
- **POST** `/v1/organizations` - Create organization
- **GET** `/v1/organizations/{orgId}` - Get organization
- **DELETE** `/v1/organizations/{orgId}` - Delete organization
- **POST** `/v1/organizations/{orgId}/members` - Add organization member
- **DELETE** `/v1/organizations/{orgId}/members/{userId}` - Remove member

## Actions

- create_user: Create user (POST /v1/users)
- list_users: List users (GET /v1/users)
- get_user: Get user (GET /v1/users/{userId})
- delete_user: Delete user (DELETE /v1/users/{userId})
- list_credentials: List user credentials (GET /v1/users/{userId}/credentials)
- delete_credential: Delete credential (DELETE /v1/users/{userId}/credentials/{credentialId})
- create_relying_party: Create relying party (POST /v1/relyingparties)
- list_relying_parties: List relying parties (GET /v1/relyingparties)
- get_relying_party: Get relying party (GET /v1/relyingparties/{rpId})
- delete_relying_party: Delete relying party (DELETE /v1/relyingparties/{rpId})
- list_organizations: List organizations (GET /v1/organizations)
- create_organization: Create organization (POST /v1/organizations)
- get_organization: Get organization (GET /v1/organizations/{orgId})
- delete_organization: Delete organization (DELETE /v1/organizations/{orgId})
- add_member: Add organization member (POST /v1/organizations/{orgId}/members)
- remove_member: Remove member (DELETE /v1/organizations/{orgId}/members/{userId})

## Fields

- `email`: string [REQUIRED] - User email
- `rp_id`: string [REQUIRED] - Relying party ID
- `rp_name`: string [REQUIRED] - Relying party name
- `org_id`: string [REQUIRED for organization] - Organization ID

## Example Request Bodies

**Create User:**
```json
{"email": "user@example.com"}
```

**Create Relying Party:**
```json
{"name": "My App", "id": "myapp.example.com", "origin": "https://myapp.example.com"}
```

**Create Organization:**
```json
{"name": "My Organization"}
```
