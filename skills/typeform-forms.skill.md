---
name: typeform-forms
description: Manage Typeform forms and responses. Use when the user mentions typeform,
  form, survey, response, quiz.
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
---

# Typeform-Forms

Manage Typeform forms and responses. Use when the user mentions typeform, form, survey, response, quiz.

## API Endpoints

- **GET** `/forms` - List forms
- **GET** `/forms/{formId}` - Get a form
- **POST** `/forms` - Create a form
- **PUT** `/forms/{formId}` - Update a form
- **DELETE** `/forms/{formId}` - Delete a form
- **GET** `/forms/{formId}/responses` - List responses
- **DELETE** `/forms/{formId}/responses` - Delete responses
- **GET** `/workspaces` - List workspaces
- **GET** `/themes` - List themes
- **GET** `/images` - List images

## Actions

- list: List forms (GET /forms)
- get_by_id: Get a form (GET /forms/{formId})
- create: Create a form (POST /forms)
- update: Update a form (PUT /forms/{formId})
- delete: Delete a form (DELETE /forms/{formId})
- list_responses: List responses (GET /forms/{formId}/responses)
- delete_responses: Delete responses (DELETE /forms/{formId}/responses)
- list_workspaces: List workspaces (GET /workspaces)
- list_themes: List themes (GET /themes)
- list_images: List images (GET /images)

## Fields

- `title`: string [REQUIRED for create]
- `fields`: array [REQUIRED for create] with `type`, `title`
- `workspace`: object [OPTIONAL] with `href`
- `theme`: object [OPTIONAL] with `href`

## Example Request Bodies

**Create Form:**
```json
{"title": "Customer Satisfaction Survey", "fields": [{"type": "rating", "title": "How satisfied are you?"}, {"type": "long_text", "title": "Any additional feedback?"}]}
```

**Update Form:**
```json
{"title": "Customer Satisfaction Survey v2"}
```
