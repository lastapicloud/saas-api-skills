---
name: tally-forms
description: Manage forms and submissions via Tally. Use when the user mentions tally,
  form, submission, response.
version: 1.0.0
skill_type: external
base_url_env: TALLY_BASE_URL
auth_env_var: TALLY_API_KEY
auth_type: bearer
triggers:
  - tally
  - form
  - submission
  - response
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TALLY_BASE_URL and TALLY_API_KEY environment variables.
---

# Tally-Forms

Manage forms and submissions via Tally. Use when the user mentions tally, form, submission, response.

## API Endpoints

- **GET** `/forms` - List forms
- **GET** `/forms/{formId}` - Get form
- **GET** `/forms/{formId}/submissions` - List submissions
- **GET** `/forms/{formId}/submissions/{submissionId}` - Get submission
- **DELETE** `/forms/{formId}/submissions/{submissionId}` - Delete submission
- **GET** `/me` - Get current user

## Actions

- list: List forms (GET /forms)
- get_by_id: Get form (GET /forms/{formId})
- list_submissions: List submissions (GET /forms/{formId}/submissions)
- get_by_id_submissions: Get submission (GET /forms/{formId}/submissions/{submissionId})
- delete: Delete submission (DELETE /forms/{formId}/submissions/{submissionId})
- list_me: Get current user (GET /me)

## Fields

- `formId`: string [REQUIRED] (form identifier)
- `submissionId`: string [REQUIRED for get/delete submission] (submission identifier)
- `status`: string [OPTIONAL] (filter by form status: "ACTIVE", "DRAFT", "CLOSED")
- `limit`: integer [OPTIONAL] (number of results to return)
- `afterDate`: string [OPTIONAL] (filter submissions after this date, ISO format)

## Example Request Bodies

**List Submissions (query params):**
```json
{
  "formId": "frm_abc123",
  "limit": 25,
  "afterDate": "2026-01-01T00:00:00Z"
}
```

**List Forms (query params):**
```json
{
  "status": "ACTIVE",
  "limit": 50
}
```
