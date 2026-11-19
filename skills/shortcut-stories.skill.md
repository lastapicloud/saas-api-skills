---
name: shortcut-stories
description: 'Create, search, and manage Shortcut stories and projects. Use when the
  user mentions shortcut, story, epic, iteration, milestone.

  '
version: 1.0.0
skill_type: external
base_url_env: SHORTCUT_BASE_URL
auth_env_var: SHORTCUT_API_TOKEN
auth_type: header
triggers:
  - shortcut
  - story
  - epic
  - iteration
  - milestone
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SHORTCUT_BASE_URL and SHORTCUT_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Shortcut-Stories

Create, search, and manage Shortcut stories and projects. Use when the user mentions shortcut, story, epic, iteration, milestone.


## API Endpoints

- **GET** `/api/v3/stories/search` - Search stories
- **GET** `/api/v3/stories/{storyId}` - Get a story
- **POST** `/api/v3/stories` - Create a story
- **PUT** `/api/v3/stories/{storyId}` - Update a story
- **DELETE** `/api/v3/stories/{storyId}` - Delete a story
- **GET** `/api/v3/projects` - List projects
- **GET** `/api/v3/epics` - List epics
- **POST** `/api/v3/epics` - Create an epic
- **GET** `/api/v3/iterations` - List iterations
- **GET** `/api/v3/workflows` - List workflows

## Actions

- search: Search stories (GET /api/v3/stories/search)
- get_by_id: Get a story (GET /api/v3/stories/{storyId})
- create: Create a story (POST /api/v3/stories)
- update: Update a story (PUT /api/v3/stories/{storyId})
- delete: Delete a story (DELETE /api/v3/stories/{storyId})
- list: List projects (GET /api/v3/projects)
- list_epics: List epics (GET /api/v3/epics)
- create_epic: Create an epic (POST /api/v3/epics)
- list_iterations: List iterations (GET /api/v3/iterations)
- list_workflows: List workflows (GET /api/v3/workflows)

## Fields

- `name`: string [REQUIRED for create] — Display name
- `story_type`: string [REQUIRED for create] (e.g., "feature", "bug", "chore") — Story resource type
- `project_id`: integer [OPTIONAL] — Project identifier
- `description`: string [OPTIONAL] — Human-readable description
- `workflow_state_id`: integer [OPTIONAL] — Workflow State unique identifier
- `estimate`: integer [OPTIONAL] — Estimate value
- `labels`: array of objects [OPTIONAL] — Labels or categories

## Example Request Bodies

**Create Story:**
```json
{"name": "Add user authentication", "story_type": "feature", "description": "Implement OAuth2 login flow", "estimate": 3}
```

**Create Epic:**
```json
{"name": "Q1 Security Improvements", "description": "All security-related work for Q1"}
```

## Response

**Storie object:**
- `id`: string — Unique storie identifier
- `name`: string — Storie name or title
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
