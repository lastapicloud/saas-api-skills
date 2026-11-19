---
name: streak-crm
description: 'Manage Streak CRM pipelines, boxes, and contacts. Use when the user
  mentions streak, CRM, pipeline, box, deal, contact.

  '
version: 1.0.0
skill_type: external
base_url_env: STREAK_BASE_URL
auth_env_var: STREAK_API_KEY
auth_type: bearer
triggers:
  - streak
  - CRM
  - pipeline
  - box
  - deal
  - contact
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires STREAK_BASE_URL and STREAK_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Streak-Crm

Manage Streak CRM pipelines, boxes, and contacts. Use when the user mentions streak, CRM, pipeline, box, deal, contact.


## API Endpoints

- **GET** `/api/v1/pipelines` - List pipelines
- **GET** `/api/v1/pipelines/{pipelineKey}` - Get a pipeline
- **POST** `/api/v1/pipelines` - Create a pipeline
- **GET** `/api/v1/pipelines/{pipelineKey}/boxes` - List boxes in a pipeline
- **GET** `/api/v1/boxes/{boxKey}` - Get a box
- **POST** `/api/v1/pipelines/{pipelineKey}/boxes` - Create a box
- **PUT** `/api/v1/boxes/{boxKey}` - Update a box
- **DELETE** `/api/v1/boxes/{boxKey}` - Delete a box
- **GET** `/api/v1/boxes/{boxKey}/contacts` - List contacts for a box
- **GET** `/api/v2/users/me` - Get current user

## Actions

- list: List pipelines (GET /api/v1/pipelines)
- get_by_id: Get a pipeline (GET /api/v1/pipelines/{pipelineKey})
- create: Create a pipeline (POST /api/v1/pipelines)
- list_boxes_pipeline: List boxes in a pipeline (GET /api/v1/pipelines/{pipelineKey}/boxes)
- get_box: Get a box (GET /api/v1/boxes/{boxKey})
- create_box: Create a box (POST /api/v1/pipelines/{pipelineKey}/boxes)
- update: Update a box (PUT /api/v1/boxes/{boxKey})
- delete: Delete a box (DELETE /api/v1/boxes/{boxKey})
- list_contacts_box: List contacts for a box (GET /api/v1/boxes/{boxKey}/contacts)
- get_current_user: Get current user (GET /api/v2/users/me)

## Fields

- `name`: string [REQUIRED for create] — Display name
- `stageKey`: string [OPTIONAL] — Stage api key or identifier
- `notes`: string [OPTIONAL] — Notes
- `assignedToSharingEntries`: array [OPTIONAL] — List of assignedToSharingEntries

## Example Request Bodies

**Create Box:**
```json
{"name": "Acme Corp Deal", "notes": "Enterprise contract negotiation"}
```

**Create Pipeline:**
```json
{"name": "Sales Pipeline"}
```

## Response

**Boxe object:**
- `id`: string — Unique boxe identifier
- `name`: string — Boxe name or title
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
