---
name: nuclino-wiki
description: 'Manage workspaces and items via Nuclino. Use when the user mentions
  nuclino, wiki, knowledge base, item, workspace, cluster.

  '
version: 1.0.0
skill_type: external
base_url_env: NUCLINO_BASE_URL
auth_env_var: NUCLINO_API_KEY
auth_type: bearer
triggers:
  - nuclino
  - wiki
  - knowledge base
  - item
  - workspace
  - cluster
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires NUCLINO_BASE_URL and NUCLINO_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Nuclino-Wiki

Manage workspaces and items via Nuclino. Use when the user mentions nuclino, wiki, knowledge base, item, workspace, cluster.


## API Endpoints

- **GET** `/v0/items` - List items
- **POST** `/v0/items` - Create item
- **GET** `/v0/items/{itemId}` - Get item
- **PUT** `/v0/items/{itemId}` - Update item
- **DELETE** `/v0/items/{itemId}` - Delete item
- **GET** `/v0/teams` - List teams
- **GET** `/v0/workspaces` - List workspaces

## Actions

- list: List items (GET /v0/items)
- create: Create item (POST /v0/items)
- get_by_id: Get item (GET /v0/items/{itemId})
- update: Update item (PUT /v0/items/{itemId})
- delete: Delete item (DELETE /v0/items/{itemId})
- list_teams: List teams (GET /v0/teams)
- list_workspaces: List workspaces (GET /v0/workspaces)

## Fields

- `object`: string [REQUIRED for create] (item) — Object
- `title`: string [REQUIRED for create] — Title or heading
- `content`: string [OPTIONAL] — Content body
- `workspaceId`: string [REQUIRED for create] — Workspace unique identifier

## Example Request Bodies

**Create an Item:**
```json
{
  "object": "item",
  "title": "Onboarding Guide",
  "content": "# Welcome\nThis guide covers the onboarding process.",
  "workspaceId": "ws_abc123"
}
```

**Update an Item:**
```json
{
  "title": "Updated Onboarding Guide",
  "content": "# Welcome\nRevised onboarding process for 2026."
}
```

## Response

**Item object:**
- `id`: string — Unique item identifier
- `name`: string — Item name or title
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
