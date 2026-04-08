---
name: qualtrics-surveys
description: Manage surveys and responses via Qualtrics. Use when the user mentions
  qualtrics, survey, response, question, experience management.
version: 1.0.0
skill_type: external
base_url_env: QUALTRICS_BASE_URL
auth_env_var: QUALTRICS_API_TOKEN
auth_type: header
triggers:
  - qualtrics
  - survey
  - response
  - question
  - experience management
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires QUALTRICS_BASE_URL and QUALTRICS_API_TOKEN environment variables.
---

# Qualtrics-Surveys

Manage surveys and responses via Qualtrics. Use when the user mentions qualtrics, survey, response, question, experience management.

## API Endpoints

- **GET** `/API/v3/surveys` - List surveys
- **POST** `/API/v3/surveys` - Create survey
- **GET** `/API/v3/surveys/{surveyId}` - Get survey
- **DELETE** `/API/v3/surveys/{surveyId}` - Delete survey
- **POST** `/API/v3/surveys/{surveyId}/export-responses` - Export responses
- **GET** `/API/v3/surveys/{surveyId}/questions` - List questions
- **POST** `/API/v3/surveys/{surveyId}/questions` - Create question
- **GET** `/API/v3/directories/{directoryId}/mailinglists` - List mailing lists
- **GET** `/distributions` - Get distributions for survey
- **POST** `/distributions` - Generate distribution links
- **POST** `/eventsubscriptions/` - Triggers when a response is submitted to a qualtrics survey
- **GET** `/distributions/{DistributionId}/links` - Retrieve distribution links
- **GET** `/eventsubscriptions/{SubscriptionId}` - Get event subscriptions
- **GET** `/survey-definitions/{SurveyId}` - Get survey
- **DELETE** `/eventsubscriptions/` - Remove subscription to response event

## Actions

- list: List surveys (GET /API/v3/surveys)
- create: Create survey (POST /API/v3/surveys)
- get_by_id: Get survey (GET /API/v3/surveys/{surveyId})
- delete: Delete survey (DELETE /API/v3/surveys/{surveyId})
- create_export_responses: Export responses (POST /API/v3/surveys/{surveyId}/export-responses)
- list_questions: List questions (GET /API/v3/surveys/{surveyId}/questions)
- create_questions: Create question (POST /API/v3/surveys/{surveyId}/questions)
- list_mailinglists: List mailing lists (GET /API/v3/directories/{directoryId}/mailinglists)
- list_distributions: Get distributions for survey (GET /distributions)
- create_distributions: Generate distribution links (POST /distributions)
- create_eventsubscriptions: Triggers when a response is submitted to a qualtrics survey (POST /eventsubscriptions/)
- list_links: Retrieve distribution links (GET /distributions/{DistributionId}/links)
- get_by_id_eventsubscriptions: Get event subscriptions (GET /eventsubscriptions/{SubscriptionId})
- get_by_id_survey_definitions: Get survey (GET /survey-definitions/{SurveyId})
- delete_eventsubscriptions: Remove subscription to response event (DELETE /eventsubscriptions/)

## Fields

- `SurveyName`: string [REQUIRED for create]
- `Language`: string [REQUIRED for create]
- `ProjectCategory`: string [OPTIONAL]

## Example Request Bodies

**Create Survey:**
```json
{"SurveyName": "Customer Satisfaction Q1", "Language": "EN", "ProjectCategory": "CORE"}
```

**Create Question:**
```json
{"QuestionText": "How satisfied are you with our service?", "QuestionType": "MC", "Selector": "SAVR"}
