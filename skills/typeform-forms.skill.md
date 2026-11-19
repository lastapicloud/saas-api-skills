---
name: typeform-forms
description: 'Manage Typeform forms and responses. Use when the user mentions typeform,
  form, survey, response, quiz.

  '
version: 1.0.0
skill_type: external
base_url_env: TYPEFORM_BASE_URL
auth_env_var: TYPEFORM_ACCESS_TOKEN
auth_type: bearer
triggers:
  - typeform
  - form
  - survey
  - response
  - quiz
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TYPEFORM_BASE_URL and TYPEFORM_ACCESS_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Typeform-Forms

Manage Typeform forms and responses. Use when the user mentions typeform, form, survey, response, quiz.


## API Endpoints

- **GET** `/themes` - Retrieve themes
- **POST** `/themes` - Create theme
- **PUT** `/themes/{theme_id}` - Update theme
- **DELETE** `/themes/{theme_id}` - Delete theme
- **GET** `/workspaces` - Retrieve workspaces
- **POST** `/workspaces` - Create workspace
- **PATCH** `/workspaces/{workspace_id}` - Update workspace
- **DELETE** `/workspaces/{workspace_id}` - Delete workspace
- **GET** `/forms` - Retrieve forms
- **POST** `/forms` - Create form
- **PATCH** `/forms/{form_id}` - Update form (patch)
- **PUT** `/forms/{form_id}` - Update form
- **DELETE** `/forms/{form_id}/responses` - Delete responses
- **GET** `/images` - Retrieve images collection
- **POST** `/images` - Create image

## Actions

- list: Retrieve themes (GET /themes)
- create: Create theme (POST /themes)
- update: Update theme (PUT /themes/{theme_id})
- delete: Delete theme (DELETE /themes/{theme_id})
- get_retrieve_workspaces: Retrieve workspaces (GET /workspaces)
- create_workspace: Create workspace (POST /workspaces)
- update_workspace: Update workspace (PATCH /workspaces/{workspace_id})
- delete_workspace: Delete workspace (DELETE /workspaces/{workspace_id})
- get_retrieve_forms: Retrieve forms (GET /forms)
- create_form: Create form (POST /forms)
- update_form_patch: Update form (patch) (PATCH /forms/{form_id})
- update_form: Update form (PUT /forms/{form_id})
- delete_responses: Delete responses (DELETE /forms/{form_id}/responses)
- get_retrieve_images_collection: Retrieve images collection (GET /images)
- create_image: Create image (POST /images)

## Fields

- `title`: string [REQUIRED for create] — Title or heading
- `fields`: array [REQUIRED for create] with `type`, `title` — List of fields
- `workspace`: object [OPTIONAL] with `href` — Workspace configuration
- `theme`: object [OPTIONAL] with `href` — Theme configuration

## Example Request Bodies

**Create Form:**
```json
{"title": "Customer Satisfaction Survey", "fields": [{"type": "rating", "title": "How satisfied are you?"}, {"type": "long_text", "title": "Any additional feedback?"}]}
```

**Update Form:**
```json
{"title": "Customer Satisfaction Survey v2"}
```

## Response

**Theme object:**
- `id`: string — Unique theme identifier
- `name`: string — Theme name or title
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
