---
name: nimble-crm
description: "Manage contacts and deals via Nimble CRM. Use when the user mentions nimble, crm, contact, deal, person, company."
version: 1.0.0
skill_type: external
base_url_env: NIMBLE_BASE_URL
auth_env_var: NIMBLE_API_TOKEN
auth_type: bearer
triggers:
  - nimble
  - crm
  - contact
  - deal
  - person
  - company
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires NIMBLE_BASE_URL and NIMBLE_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Nimble-Crm

Manage contacts and deals via Nimble CRM. Use when the user mentions nimble, crm, contact, deal, person, company.


## API Endpoints

- **GET** `/api/v1/contacts` - List contacts
- **POST** `/api/v1/contact` - Create contact
- **GET** `/api/v1/contact/{id}` - Get contact
- **PUT** `/api/v1/contact/{id}` - Update contact
- **DELETE** `/api/v1/contact/{id}` - Delete contact
- **GET** `/api/v1/contacts/search` - Search contacts
- **GET** `/api/v1/deals` - List deals
- **POST** `/api/v1/deal` - Create deal
- **GET** `/2020-08-01/studios` - List studios in your Amazon Web Services accounts in the requested Amazon Web Services Region.
- **POST** `/2020-08-01/studios` - Create a new studio. When creating a studio, two IAM roles must be provided: the admin role and the user
- **PATCH** `/2020-08-01/studios/{studioId}` - Update a Studio resource. Currently, this operation only supports updating the displayName of your studio.
- **DELETE** `/2020-08-01/studios/{studioId}` - Delete a studio resource.
- **PUT** `/2020-08-01/studios/{studioId}/sso-configuration` - Repairs the IAM Identity Center configuration for a given studio. If the studio has a valid IAM Identity
- **GET** `/2020-08-01/eulas` - List EULAs.

## Actions

- list: List contacts (GET /api/v1/contacts)
- create: Create contact (POST /api/v1/contact)
- get_by_id: Get contact (GET /api/v1/contact/{id})
- update: Update contact (PUT /api/v1/contact/{id})
- delete: Delete contact (DELETE /api/v1/contact/{id})
- search: Search contacts (GET /api/v1/contacts/search)
- list_deals: List deals (GET /api/v1/deals)
- create_deal: Create deal (POST /api/v1/deal)
- list_studios: List studios in your Amazon Web Services accounts in the requested Amazon Web Se (GET /2020-08-01/studios)
- create_studios: Create a new studio. When creating a studio, two IAM roles must be provided: the (POST /2020-08-01/studios)
- update_studios: Update a Studio resource. Currently, this operation only supports updating the d (PATCH /2020-08-01/studios/{studioId})
- delete_studios: Delete a studio resource. (DELETE /2020-08-01/studios/{studioId})
- put_sso_configuration: Repairs the IAM Identity Center configuration for a given studio. If the studio (PUT /2020-08-01/studios/{studioId}/sso-configuration)
- list_eulas: List EULAs. (GET /2020-08-01/eulas)

## Fields

- `fields`: object [REQUIRED for create]
- `record_type`: string [REQUIRED for create] (person or company)
- `query`: string [REQUIRED for search]

## Example Request Bodies

**Create Contact:**
```json
{"fields": {"first name": [{"value": "Alex"}], "last name": [{"value": "Johnson"}], "email": [{"value": "alex@example.com"}]}, "record_type": "person"}
```

**Create Deal:**
```json
{"fields": {"name": [{"value": "Enterprise License"}], "amount": [{"value": "15000"}], "stage": [{"value": "Proposal"}]}}
```

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request — missing required field, wrong type, or constraint violation |
| 401 | Authentication failed — check API credentials |
| 403 | Forbidden — insufficient permissions |
| 404 | Resource not found |
| 429 | Rate limited — retry after delay |
| 500 | Server error |
