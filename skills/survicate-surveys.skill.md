---
name: survicate-surveys
description: Manage surveys and responses via Survicate. Use when the user mentions
  survicate, survey, feedback, response, nps.
version: 1.0.0
skill_type: external
base_url_env: SURVICATE_BASE_URL
auth_env_var: SURVICATE_API_KEY
auth_type: header
triggers:
  - survicate
  - survey
  - feedback
  - response
  - nps
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SURVICATE_BASE_URL and SURVICATE_API_KEY environment variables.
---

# Survicate-Surveys

Manage surveys and responses via Survicate. Use when the user mentions survicate, survey, feedback, response, nps.

## API Endpoints

- **GET** `/v1/surveys` - List surveys
- **GET** `/v1/surveys/{surveyId}` - Get survey
- **GET** `/v1/surveys/{surveyId}/responses` - List responses
- **GET** `/v1/surveys/{surveyId}/questions` - List questions
- **GET** `/v1/respondents` - List respondents
- **GET** `/v1/respondents/{respondentId}` - Get respondent

## Actions

- list: List surveys (GET /v1/surveys)
- get_by_id: Get survey (GET /v1/surveys/{surveyId})
- list_responses: List responses (GET /v1/surveys/{surveyId}/responses)
- list_questions: List questions (GET /v1/surveys/{surveyId}/questions)
- list_respondents: List respondents (GET /v1/respondents)
- get_by_id_respondents: Get respondent (GET /v1/respondents/{respondentId})

## Fields

- `surveyId`: string [REQUIRED] (survey identifier)
- `since`: string [OPTIONAL] (date filter in ISO format)
- `until`: string [OPTIONAL] (end date filter in ISO format)
- `respondentId`: string [REQUIRED for get respondent] (respondent identifier)
- `limit`: integer [OPTIONAL] (number of results to return)
- `offset`: integer [OPTIONAL] (pagination offset)

## Example Request Bodies

**List Responses (query params):**
```json
{
  "surveyId": "srv_abc123",
  "since": "2026-01-01T00:00:00Z",
  "limit": 50
}
```

**List Respondents (query params):**
```json
{
  "since": "2026-01-01T00:00:00Z",
  "until": "2026-03-31T23:59:59Z",
  "limit": 100
}
```
