---
name: streak-crm
description: Manage Streak CRM pipelines, boxes, and contacts. Use when the user mentions
  streak, CRM, pipeline, box, deal, contact.
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
- list_boxes: List boxes in a pipeline (GET /api/v1/pipelines/{pipelineKey}/boxes)
- get_by_id_boxes: Get a box (GET /api/v1/boxes/{boxKey})
- create_boxes: Create a box (POST /api/v1/pipelines/{pipelineKey}/boxes)
- update: Update a box (PUT /api/v1/boxes/{boxKey})
- delete: Delete a box (DELETE /api/v1/boxes/{boxKey})
- list_contacts: List contacts for a box (GET /api/v1/boxes/{boxKey}/contacts)
- list_me: Get current user (GET /api/v2/users/me)

## Fields

- `name`: string [REQUIRED for create]
- `stageKey`: string [OPTIONAL]
- `notes`: string [OPTIONAL]
- `assignedToSharingEntries`: array [OPTIONAL]

## Example Request Bodies

**Create Box:**
```json
{"name": "Acme Corp Deal", "notes": "Enterprise contract negotiation"}
```

**Create Pipeline:**
```json
{"name": "Sales Pipeline"}
```
