---
name: formstack-forms
description: Manage forms and submissions via Formstack. Use when the user mentions
  formstack, form, submission, field, survey.
version: 1.0.0
skill_type: external
base_url_env: FORMSTACK_BASE_URL
auth_env_var: FORMSTACK_ACCESS_TOKEN
auth_type: bearer
triggers:
  - formstack
  - form
  - submission
  - field
  - survey
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FORMSTACK_BASE_URL and FORMSTACK_ACCESS_TOKEN environment
  variables.
---

# Formstack-Forms

Manage forms and submissions via Formstack. Use when the user mentions formstack, form, submission, field, survey.

## API Endpoints

- **GET** `/api/v2/form.json` - List forms
- **POST** `/api/v2/form.json` - Create form
- **GET** `/api/v2/form/{id}.json` - Get form
- **PUT** `/api/v2/form/{id}.json` - Update form
- **DELETE** `/api/v2/form/{id}.json` - Delete form
- **GET** `/api/v2/form/{id}/submission.json` - List submissions
- **POST** `/api/v2/form/{id}/submission.json` - Create submission
- **GET** `/api/v2/submission/{id}.json` - Get submission

## Actions

- list: List forms (GET /api/v2/form.json)
- create: Create form (POST /api/v2/form.json)
- list_form: Get form (GET /api/v2/form/{id}.json)
- put_form: Update form (PUT /api/v2/form/{id}.json)
- delete_form: Delete form (DELETE /api/v2/form/{id}.json)
- list_submission_json: List submissions (GET /api/v2/form/{id}/submission.json)
- create_submission_json: Create submission (POST /api/v2/form/{id}/submission.json)
- list_submission: Get submission (GET /api/v2/submission/{id}.json)

## Fields

- `name`: string [REQUIRED for create]
- `fields`: array [OPTIONAL]

## Example Request Bodies

**Create Form:**
```json
{"name": "Contact Us Form"}
```

**Create Submission:**
```json
{"field_12345": "John Doe", "field_12346": "john@example.com", "field_12347": "How can I help?"}
