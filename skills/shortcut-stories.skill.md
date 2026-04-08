---
name: shortcut-stories
description: Create, search, and manage Shortcut stories and projects. Use when the
  user mentions shortcut, story, epic, iteration, milestone.
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
- create_epics: Create an epic (POST /api/v3/epics)
- list_iterations: List iterations (GET /api/v3/iterations)
- list_workflows: List workflows (GET /api/v3/workflows)

## Fields

- `name`: string [REQUIRED for create]
- `story_type`: string [REQUIRED for create] (e.g., "feature", "bug", "chore")
- `project_id`: integer [OPTIONAL]
- `description`: string [OPTIONAL]
- `workflow_state_id`: integer [OPTIONAL]
- `estimate`: integer [OPTIONAL]
- `labels`: array of objects [OPTIONAL]

## Example Request Bodies

**Create Story:**
```json
{"name": "Add user authentication", "story_type": "feature", "description": "Implement OAuth2 login flow", "estimate": 3}
```

**Create Epic:**
```json
{"name": "Q1 Security Improvements", "description": "All security-related work for Q1"}
```
