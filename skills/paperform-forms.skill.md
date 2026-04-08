---
name: paperform-forms
description: Manage forms and submissions via Paperform. Use when the user mentions
  paperform, form, submission, survey.
version: 1.0.0
skill_type: external
base_url_env: PAPERFORM_BASE_URL
auth_env_var: PAPERFORM_API_KEY
auth_type: bearer
triggers:
  - paperform
  - form
  - submission
  - survey
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PAPERFORM_BASE_URL and PAPERFORM_API_KEY environment variables.
---

# Paperform-Forms

Manage forms and submissions via Paperform. Use when the user mentions paperform, form, submission, survey.

## API Endpoints

- **GET** `/v1/forms` - List forms
- **GET** `/v1/forms/{formSlug}` - Get form
- **GET** `/v1/forms/{formSlug}/submissions` - List submissions
- **GET** `/v1/submissions/{submissionId}` - Get submission
- **DELETE** `/v1/submissions/{submissionId}` - Delete submission
- **PATCH** `/v1/forms/{formSlug}/submissions/{submissionId}` - Update submission

## Actions

- list: List forms (GET /v1/forms)
- get_by_id: Get form (GET /v1/forms/{formSlug})
- list_submissions: List submissions (GET /v1/forms/{formSlug}/submissions)
- get_by_id_submissions: Get submission (GET /v1/submissions/{submissionId})
- delete: Delete submission (DELETE /v1/submissions/{submissionId})
- update: Update submission (PATCH /v1/forms/{formSlug}/submissions/{submissionId})

## Fields

- `formSlug`: string [REQUIRED]

## Example Request Bodies

**Update Submission:**
```json
{"formSlug": "customer-feedback", "data": {"rating": 5, "comments": "Great service!"}}
```

**Query Submissions (via params):**
```json
{"formSlug": "customer-feedback"}
```
