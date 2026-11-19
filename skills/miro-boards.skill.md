---
name: miro-boards
description: 'Manage boards and items via Miro. Use when the user mentions miro, board,
  whiteboard, sticky note, widget, collaboration.

  '
version: 1.0.0
skill_type: external
base_url_env: MIRO_BASE_URL
auth_env_var: MIRO_ACCESS_TOKEN
auth_type: bearer
triggers:
  - miro
  - board
  - whiteboard
  - sticky note
  - widget
  - collaboration
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MIRO_BASE_URL and MIRO_ACCESS_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Miro-Boards

Manage boards and items via Miro. Use when the user mentions miro, board, whiteboard, sticky note, widget, collaboration.


## API Endpoints

- **GET** `/v2/boards` - List boards
- **POST** `/v2/boards` - Create board
- **GET** `/v2/boards/{board_id}` - Get board
- **GET** `/v2/boards/{board_id}/items` - List items
- **POST** `/v2/boards/{board_id}/sticky_notes` - Create sticky note
- **POST** `/v2/boards/{board_id}/shapes` - Create shape
- **POST** `/v2/boards/{board_id}/texts` - Create text
- **GET** `/v2/boards/{board_id}/members` - List members

## Actions

- list: List boards (GET /v2/boards)
- create: Create board (POST /v2/boards)
- get_by_id: Get board (GET /v2/boards/{board_id})
- list_items: List items (GET /v2/boards/{board_id}/items)
- create_sticky_note: Create sticky note (POST /v2/boards/{board_id}/sticky_notes)
- create_shape: Create shape (POST /v2/boards/{board_id}/shapes)
- create_text: Create text (POST /v2/boards/{board_id}/texts)
- list_members: List members (GET /v2/boards/{board_id}/members)

## Fields

- `name`: string [REQUIRED for create] — Display name
- `description`: string [OPTIONAL] — Human-readable description
- `data`: object [REQUIRED for sticky_note] (content) — Request payload data

## Example Request Bodies

**Create Board:**
```json
{"name": "Sprint Planning Board", "description": "Board for Q1 sprint planning sessions"}
```

**Create Sticky Note:**
```json
{"data": {"content": "Review API performance metrics"}, "position": {"x": 100, "y": 200}}
```

## Response

**Board object:**
- `id`: string — Unique board identifier
- `name`: string — Board name or title
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
