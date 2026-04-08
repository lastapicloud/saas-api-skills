---
name: surveymonkey-surveys
description: Manage surveys and responses via SurveyMonkey. Use when the user mentions
  surveymonkey, survey, response, question, collector.
version: 1.0.0
skill_type: external
base_url_env: SURVEYMONKEY_BASE_URL
auth_env_var: SURVEYMONKEY_ACCESS_TOKEN
auth_type: bearer
triggers:
  - surveymonkey
  - survey
  - response
  - question
  - collector
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SURVEYMONKEY_BASE_URL and SURVEYMONKEY_ACCESS_TOKEN environment
  variables.
---

# Surveymonkey-Surveys

Manage surveys and responses via SurveyMonkey. Use when the user mentions surveymonkey, survey, response, question, collector.

## API Endpoints

- **GET** `/v3/surveys` - List surveys
- **POST** `/v3/surveys` - Create survey
- **GET** `/v3/surveys/{id}` - Get survey
- **DELETE** `/v3/surveys/{id}` - Delete survey
- **GET** `/v3/surveys/{id}/responses/bulk` - List responses
- **GET** `/v3/surveys/{id}/pages` - List pages
- **GET** `/v3/surveys/{id}/collectors` - List collectors
- **POST** `/v3/surveys/{id}/collectors` - Create collector

## Actions

- list: List surveys (GET /v3/surveys)
- create: Create survey (POST /v3/surveys)
- get_by_id: Get survey (GET /v3/surveys/{id})
- delete: Delete survey (DELETE /v3/surveys/{id})
- list_bulk: List responses (GET /v3/surveys/{id}/responses/bulk)
- list_pages: List pages (GET /v3/surveys/{id}/pages)
- list_collectors: List collectors (GET /v3/surveys/{id}/collectors)
- create_collectors: Create collector (POST /v3/surveys/{id}/collectors)

## Fields

- `title`: string [REQUIRED for create]

## Example Request Bodies

**Create Survey:**
```json
{"title": "Customer Feedback Survey 2026"}
```

**Create Collector:**
```json
{"type": "weblink", "name": "Email Campaign Link"}
