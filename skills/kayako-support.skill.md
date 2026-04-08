---
name: kayako-support
description: Manage tickets and users via Kayako. Use when the user mentions kayako,
  support, ticket, helpdesk, customer.
version: 1.0.0
skill_type: external
base_url_env: KAYAKO_BASE_URL
auth_env_var: KAYAKO_API_TOKEN
auth_type: bearer
triggers:
  - kayako
  - support
  - ticket
  - helpdesk
  - customer
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires KAYAKO_BASE_URL and KAYAKO_API_TOKEN environment variables.
---

# Kayako-Support

Manage tickets and users via Kayako. Use when the user mentions kayako, support, ticket, helpdesk, customer.

## API Endpoints

- **GET** `/api/v1/cases` - List cases
- **POST** `/api/v1/cases` - Create case
- **GET** `/api/v1/cases/{id}` - Get case
- **PUT** `/api/v1/cases/{id}` - Update case
- **GET** `/api/v1/users` - List users
- **POST** `/api/v1/users` - Create user
- **GET** `/api/v1/teams` - List teams
- **POST** `/api/v1/cases/{id}/notes` - Add note to case

## Actions

- list: List cases (GET /api/v1/cases)
- create: Create case (POST /api/v1/cases)
- get_by_id: Get case (GET /api/v1/cases/{id})
- update: Update case (PUT /api/v1/cases/{id})
- list_users: List users (GET /api/v1/users)
- create_users: Create user (POST /api/v1/users)
- list_teams: List teams (GET /api/v1/teams)
- create_notes: Add note to case (POST /api/v1/cases/{id}/notes)

## Fields

- `subject`: string [REQUIRED for create]
- `requester_id`: integer [REQUIRED for create]
- `channel`: string [OPTIONAL]

## Example Request Bodies

**Create Case:**
```json
{"subject": "Cannot access my account", "requester_id": 12345, "channel": "email"}
```

**Add Note to Case:**
```json
{"content": "Customer was contacted via phone and issue was escalated to tier 2."}
```
