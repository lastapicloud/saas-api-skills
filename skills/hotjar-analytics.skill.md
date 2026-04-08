---
name: hotjar-analytics
description: Access heatmaps and surveys via Hotjar. Use when the user mentions hotjar,
  heatmap, survey, feedback, recording, analytics.
version: 1.0.0
skill_type: external
base_url_env: HOTJAR_BASE_URL
auth_env_var: HOTJAR_API_TOKEN
auth_type: bearer
triggers:
  - hotjar
  - heatmap
  - survey
  - feedback
  - recording
  - analytics
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires HOTJAR_BASE_URL and HOTJAR_API_TOKEN environment variables.
---

# Hotjar-Analytics

Access heatmaps and surveys via Hotjar. Use when the user mentions hotjar, heatmap, survey, feedback, recording, analytics.

## API Endpoints

- **GET** `/api/v2/sites` - List sites
- **GET** `/api/v2/sites/{siteId}` - Get site
- **GET** `/api/v2/sites/{siteId}/feedback` - List feedback
- **GET** `/api/v2/sites/{siteId}/surveys` - List surveys
- **POST** `/api/v2/sites/{siteId}/surveys` - Create survey
- **GET** `/api/v2/sites/{siteId}/surveys/{surveyId}/responses` - List survey responses

## Actions

- list: List sites (GET /api/v2/sites)
- get_by_id: Get site (GET /api/v2/sites/{siteId})
- list_feedback: List feedback (GET /api/v2/sites/{siteId}/feedback)
- list_surveys: List surveys (GET /api/v2/sites/{siteId}/surveys)
- create: Create survey (POST /api/v2/sites/{siteId}/surveys)
- list_responses: List survey responses (GET /api/v2/sites/{siteId}/surveys/{surveyId}/responses)

## Fields

- `name`: string [REQUIRED for create_survey]
- `questions`: array [OPTIONAL]

## Example Request Bodies

**Create Survey:**
```json
{"name": "User Satisfaction Survey", "questions": [{"type": "rating", "text": "How would you rate your experience?"}]}
```

**List Feedback (query):**
```json
{"siteId": "123456", "limit": 50, "offset": 0}
```
