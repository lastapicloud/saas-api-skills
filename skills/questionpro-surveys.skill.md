---
name: questionpro-surveys
description: Manage surveys and responses via QuestionPro. Use when the user mentions
  questionpro, survey, response, question, poll.
version: 1.0.0
skill_type: external
base_url_env: QUESTIONPRO_BASE_URL
auth_env_var: QUESTIONPRO_API_KEY
auth_type: header
triggers:
  - questionpro
  - survey
  - response
  - question
  - poll
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires QUESTIONPRO_BASE_URL and QUESTIONPRO_API_KEY environment variables.
---

# Questionpro-Surveys

Manage surveys and responses via QuestionPro. Use when the user mentions questionpro, survey, response, question, poll.

## API Endpoints

- **GET** `/api/v2/surveys` - List surveys
- **POST** `/api/v2/surveys` - Create survey
- **GET** `/api/v2/surveys/{surveyID}` - Get survey
- **DELETE** `/api/v2/surveys/{surveyID}` - Delete survey
- **GET** `/api/v2/surveys/{surveyID}/responses` - List responses
- **GET** `/api/v2/surveys/{surveyID}/questions` - List questions
- **POST** `/api/v2/surveys/{surveyID}/questions` - Add question

## Actions

- list: List surveys (GET /api/v2/surveys)
- create: Create survey (POST /api/v2/surveys)
- get_by_id: Get survey (GET /api/v2/surveys/{surveyID})
- delete: Delete survey (DELETE /api/v2/surveys/{surveyID})
- list_responses: List responses (GET /api/v2/surveys/{surveyID}/responses)
- list_questions: List questions (GET /api/v2/surveys/{surveyID}/questions)
- create_questions: Add question (POST /api/v2/surveys/{surveyID}/questions)

## Fields

- `name`: string [REQUIRED for create survey]
- `type`: string [OPTIONAL] (survey type)
- `surveyID`: integer [REQUIRED for get/delete/list responses]
- `description`: string [OPTIONAL] (survey description)
- `questionText`: string [REQUIRED for add question] (question text)
- `questionType`: string [REQUIRED for add question] ("single_choice", "multiple_choice", "text", "rating")
- `choices`: array [OPTIONAL for add question] (answer choices for choice-based questions)
- `isRequired`: boolean [OPTIONAL] (whether the question is required)

## Example Request Bodies

**Create a Survey:**
```json
{
  "name": "Customer Satisfaction Q1 2026",
  "description": "Quarterly customer feedback survey",
  "type": "survey"
}
```

**Add a Question:**
```json
{
  "questionText": "How satisfied are you with our service?",
  "questionType": "rating",
  "isRequired": true
}
```
