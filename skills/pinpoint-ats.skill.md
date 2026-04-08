---
name: pinpoint-ats
description: Manage Pinpoint ATS candidates, jobs, and applications. Use when the
  user mentions pinpoint, candidate, job, ATS, hiring, application.
version: 1.0.0
skill_type: external
base_url_env: PINPOINT_BASE_URL
auth_env_var: PINPOINT_API_KEY
auth_type: header
triggers:
  - pinpoint
  - candidate
  - job
  - ATS
  - hiring
  - application
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PINPOINT_BASE_URL and PINPOINT_API_KEY environment variables.
---

# Pinpoint-Ats

Manage Pinpoint ATS candidates, jobs, and applications. Use when the user mentions pinpoint, candidate, job, ATS, hiring, application.

## API Endpoints

- **GET** `/api/v1/candidates` - List candidates
- **GET** `/api/v1/candidates/{candidateId}` - Get a candidate
- **POST** `/api/v1/candidates` - Create a candidate
- **PATCH** `/api/v1/candidates/{candidateId}` - Update a candidate
- **GET** `/api/v1/jobs` - List jobs
- **GET** `/api/v1/jobs/{jobId}` - Get a job
- **POST** `/api/v1/jobs` - Create a job
- **GET** `/api/v1/applications` - List applications
- **GET** `/api/v1/departments` - List departments
- **GET** `/api/v1/stages` - List stages
- **GET** `/v1/recommenders` - Retrieves information about all the recommender model configurations that are associated with your Amazon Pinpoint
- **POST** `/v1/recommenders` - Creates an Amazon Pinpoint configuration for a recommender model.
- **PUT** `/v1/recommenders/{recommender-id}` - Updates an Amazon Pinpoint configuration for a recommender model.
- **DELETE** `/v1/recommenders/{recommender-id}` - Deletes an Amazon Pinpoint configuration for a recommender model.
- **GET** `/v1/templates` - Retrieves information about all the message templates that are associated with your Amazon Pinpoint account.

## Actions

- list: List candidates (GET /api/v1/candidates)
- get_by_id: Get a candidate (GET /api/v1/candidates/{candidateId})
- create: Create a candidate (POST /api/v1/candidates)
- update: Update a candidate (PATCH /api/v1/candidates/{candidateId})
- list_jobs: List jobs (GET /api/v1/jobs)
- get_by_id_jobs: Get a job (GET /api/v1/jobs/{jobId})
- create_jobs: Create a job (POST /api/v1/jobs)
- list_applications: List applications (GET /api/v1/applications)
- list_departments: List departments (GET /api/v1/departments)
- list_stages: List stages (GET /api/v1/stages)
- list_recommenders: Retrieves information about all the recommender model configurations that are as (GET /v1/recommenders)
- create_recommenders: Creates an Amazon Pinpoint configuration for a recommender model. (POST /v1/recommenders)
- update_recommenders: Updates an Amazon Pinpoint configuration for a recommender model. (PUT /v1/recommenders/{recommender-id})
- delete: Deletes an Amazon Pinpoint configuration for a recommender model. (DELETE /v1/recommenders/{recommender-id})
- list_templates: Retrieves information about all the message templates that are associated with y (GET /v1/templates)

## Fields

- `first_name`: string [REQUIRED for create]
- `last_name`: string [REQUIRED for create]
- `email`: string [REQUIRED for create]
- `phone`: string [OPTIONAL]

## Example Request Bodies

**Create Candidate:**
```json
{"first_name": "Emily", "last_name": "Chen", "email": "emily.chen@example.com", "phone": "+1-555-0123"}
```

**Create Job:**
```json
{"title": "Product Manager", "department_id": "dept-123", "status": "published"}
```
