---
name: ping-identity-auth
description: 'Manage users and groups via PingOne. Use when the user mentions ping
  identity, pingone, ping, auth, user, identity, sso.

  '
version: 1.0.0
skill_type: external
base_url_env: PING_IDENTITY_BASE_URL
auth_env_var: PING_IDENTITY_ACCESS_TOKEN
auth_type: bearer
triggers:
  - ping identity
  - pingone
  - ping
  - auth
  - user
  - identity
  - sso
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: 'Requires PING_IDENTITY_BASE_URL and PING_IDENTITY_ACCESS_TOKEN environment
  variables.

  '
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Ping-Identity-Auth

Manage users and groups via PingOne. Use when the user mentions ping identity, pingone, ping, auth, user, identity, sso.


## API Endpoints

- **GET** `/environments` - This PingOne collection contains only the requests without documentation
- **POST** `/environments` - This PingOne collection contains only the requests without documentation
- **PUT** `/environments/{envID}/billOfMaterials` - This PingOne collection contains only the requests without documentation
- **DELETE** `/environments/{envID}` - This PingOne collection contains only the requests without documentation
- **PATCH** `/environments/{envID}/templates/{templateName}/contents` - This PingOne collection contains only the requests without documentation
- **GET** `/organizations` - This PingOne collection contains only the requests without documentation
- **PUT** `/organizations/{orgID}/licenses/{licenseID}/name` - This PingOne collection contains only the requests without documentation
- **GET** `/roles` - This PingOne collection contains only the requests without documentation
- **GET** `/roles/{roleID}` - This PingOne collection contains only the requests without documentation

## Actions

- list: This PingOne collection contains only the requests without documentation (GET /environments)
- create: This PingOne collection contains only the requests without documentation (POST /environments)
- put_billofmaterials: This PingOne collection contains only the requests without documentation (PUT /environments/{envID}/billOfMaterials)
- delete: This PingOne collection contains only the requests without documentation (DELETE /environments/{envID})
- patch_contents: This PingOne collection contains only the requests without documentation (PATCH /environments/{envID}/templates/{templateName}/contents)
- get_this_pingone_collection_contains: This PingOne collection contains only the requests without documentation (GET /organizations)
- put_name: This PingOne collection contains only the requests without documentation (PUT /organizations/{orgID}/licenses/{licenseID}/name)
- list_roles: This PingOne collection contains only the requests without documentation (GET /roles)
- get_by_id: This PingOne collection contains only the requests without documentation (GET /roles/{roleID})

## Fields

- `email`: string [REQUIRED for create] — Email address
- `username`: string [REQUIRED for create] — Username
- `name`: object [OPTIONAL] (given, family) — Display name

## Example Request Bodies

**Create User:**
```json
{"email": "jdoe@example.com", "username": "jdoe", "name": {"given": "John", "family": "Doe"}}
```

**Update User:**
```json
{"email": "john.doe@example.com", "name": {"given": "John", "family": "Doe-Smith"}}
```

## Response

**Environment object:**
- `id`: string — Unique environment identifier
- `name`: string — Environment name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 404 | Resource not found — check the ID or identifier |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
