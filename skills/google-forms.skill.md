---
name: google-forms
description: Manage forms and responses via Google Forms. Use when the user mentions
  google forms, form, response, quiz, survey.
version: 1.0.0
skill_type: external
base_url_env: GOOGLE_FORMS_BASE_URL
auth_env_var: GOOGLE_API_TOKEN
auth_type: bearer
triggers:
  - google forms
  - form
  - response
  - quiz
  - survey
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GOOGLE_FORMS_BASE_URL and GOOGLE_API_TOKEN environment variables.
---

# Google-Forms

Manage forms and responses via Google Forms. Use when the user mentions google forms, form, response, quiz, survey.

## API Endpoints

- **POST** `/v1/forms` - Create form
- **GET** `/v1/forms/{formId}` - Get form
- **PATCH** `/v1/forms/{formId}` - Update form
- **GET** `/v1/forms/{formId}/responses` - List responses
- **GET** `/v1/forms/{formId}/responses/{responseId}` - Get response
- **POST** `/v1/forms/{formId}:batchUpdate` - Batch update form
- **GET** `/v3/{name}` - Returns a reconciliation report.
- **PATCH** `/v3/{name}` - Updates a brand.
- **DELETE** `/v3/{name}` - Deletes an account link.
- **GET** `/v3/{parent}/accountLinks` - Returns the account links for a Hotel Center account.
- **POST** `/v3/{parent}/accountLinks` - Creates a new account link between a Hotel Center account and a Google Ads account.
- **GET** `/v3/{parent}/brands` - Returns the brands for a partner account.
- **POST** `/v3/{parent}/brands` - Creates a new brand. Because Google detects brands from your existing properties, you only need this operation when you
- **GET** `/v3/{parent}/icons` - Returns the `Icon`s for a partner account.
- **POST** `/v3/{parent}/icons` - Uploads a new icon and starts its review process. Generates an `icon_id` and includes it in the icon's resource name,

## Actions

- create: Create form (POST /v1/forms)
- get_by_id: Get form (GET /v1/forms/{formId})
- update: Update form (PATCH /v1/forms/{formId})
- list: List responses (GET /v1/forms/{formId}/responses)
- get_by_id_responses: Get response (GET /v1/forms/{formId}/responses/{responseId})
- create_forms: Batch update form (POST /v1/forms/{formId}:batchUpdate)
- get_by_id_v3: Returns a reconciliation report. (GET /v3/{name})
- update_v3: Updates a brand. (PATCH /v3/{name})
- delete: Deletes an account link. (DELETE /v3/{name})
- list_accountlinks: Returns the account links for a Hotel Center account. (GET /v3/{parent}/accountLinks)
- create_accountlinks: Creates a new account link between a Hotel Center account and a Google Ads accou (POST /v3/{parent}/accountLinks)
- list_brands: Returns the brands for a partner account. (GET /v3/{parent}/brands)
- create_brands: Creates a new brand. Because Google detects brands from your existing properties (POST /v3/{parent}/brands)
- list_icons: Returns the `Icon`s for a partner account. (GET /v3/{parent}/icons)
- create_icons: Uploads a new icon and starts its review process. Generates an `icon_id` and inc (POST /v3/{parent}/icons)

## Fields

- `info`: object [REQUIRED for create] (title, documentTitle)
- `formId`: string [REQUIRED]

## Example Request Bodies

**Create Form:**
```json
{"info": {"title": "Customer Feedback Survey", "documentTitle": "Q1 Feedback"}}
```

**Batch Update Form:**
```json
{"requests": [{"createItem": {"item": {"title": "How satisfied are you?", "questionItem": {"question": {"required": true, "scaleQuestion": {"low": 1, "high": 5}}}}, "location": {"index": 0}}}]}
```
