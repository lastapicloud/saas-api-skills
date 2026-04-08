---
name: jotform-forms
description: Manage forms and submissions via JotForm. Use when the user mentions
  jotform, form, submission, survey, field.
version: 1.0.0
skill_type: external
base_url_env: JOTFORM_BASE_URL
auth_env_var: JOTFORM_API_KEY
auth_type: header
triggers:
  - jotform
  - form
  - submission
  - survey
  - field
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires JOTFORM_BASE_URL and JOTFORM_API_KEY environment variables.
---

# Jotform-Forms

Manage forms and submissions via JotForm. Use when the user mentions jotform, form, submission, survey, field.

## API Endpoints

- **GET** `/user/forms` - List forms
- **GET** `/form/{formId}` - Get form
- **GET** `/form/{formId}/questions` - List questions
- **GET** `/form/{formId}/submissions` - List submissions
- **POST** `/form/{formId}/submissions` - Create submission
- **GET** `/submission/{submissionId}` - Get submission
- **DELETE** `/submission/{submissionId}` - Delete submission
- **POST** `/user/forms` - Create form

## Actions

- list: List forms (GET /user/forms)
- get_by_id: Get form (GET /form/{formId})
- list_questions: List questions (GET /form/{formId}/questions)
- list_submissions: List submissions (GET /form/{formId}/submissions)
- create: Create submission (POST /form/{formId}/submissions)
- get_by_id_submission: Get submission (GET /submission/{submissionId})
- delete: Delete submission (DELETE /submission/{submissionId})
- create_forms: Create form (POST /user/forms)

## Fields

- `questions`: array [OPTIONAL for create]
- `submission`: object [REQUIRED for create_submission]

## Example Request Bodies

**Create Submission:**
```json
{"submission": {"3": "John Doe", "4": "john@example.com", "5": "Looking forward to hearing from you"}}
```

**Create Form:**
```json
{"questions": [{"type": "control_textbox", "text": "Full Name"}, {"type": "control_email", "text": "Email Address"}]}
```
