---
name: greenhouse-ats
description: Manage candidates, jobs, and applications in Greenhouse ATS. Use when
  the user mentions greenhouse, greenhouse candidate, greenhouse job, greenhouse application,
  greenhouse hiring.
version: 1.0.0
skill_type: external
base_url_env: GREENHOUSE_BASE_URL
auth_env_var: GREENHOUSE_API_KEY
auth_type: basic
triggers:
  - greenhouse
  - greenhouse candidate
  - greenhouse job
  - greenhouse application
  - greenhouse hiring
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires GREENHOUSE_BASE_URL and GREENHOUSE_API_KEY environment variables.
---

# Greenhouse-Ats

Manage candidates, jobs, and applications in Greenhouse ATS. Use when the user mentions greenhouse, greenhouse candidate, greenhouse job, greenhouse application, greenhouse hiring.

## API Endpoints

- **GET** `/v1/candidates` - List candidates
- **POST** `/v1/candidates` - Create a candidate
- **GET** `/v1/candidates/{id}` - Get a candidate by ID
- **PATCH** `/v1/candidates/{id}` - Update a candidate
- **GET** `/v1/jobs` - List jobs
- **GET** `/v1/jobs/{id}` - Get a job by ID
- **GET** `/v1/applications` - List applications
- **POST** `/v1/applications` - Create an application
- **GET** `/v1/applications/{id}` - Get an application by ID
- **PATCH** `/v1/applications/{id}/advance` - Advance an application
- **GET** `/v1/candidates/`

## Actions

- list: List candidates (GET /v1/candidates)
- create: Create a candidate (POST /v1/candidates)
- get_by_id: Get a candidate by ID (GET /v1/candidates/{id})
- update: Update a candidate (PATCH /v1/candidates/{id})
- list_jobs: List jobs (GET /v1/jobs)
- get_by_id_jobs: Get a job by ID (GET /v1/jobs/{id})
- list_applications: List applications (GET /v1/applications)
- create_applications: Create an application (POST /v1/applications)
- get_by_id_applications: Get an application by ID (GET /v1/applications/{id})
- patch_advance: Advance an application (PATCH /v1/applications/{id}/advance)
- list_candidates: GET /v1/candidates/ (GET /v1/candidates/)

## Fields

- `id`: integer [REQUIRED for get_candidate, update_candidate, get_job, get_application, advance_application] (record ID)
- `first_name`: string [REQUIRED for create_candidate] (first name)
- `last_name`: string [REQUIRED for create_candidate] (last name)
- `email_addresses`: array [OPTIONAL] (email addresses with value and type fields)
- `phone_numbers`: array [OPTIONAL] (phone numbers with value and type fields)
- `job_id`: integer [REQUIRED for create_application] (job ID)
- `candidate_id`: integer [REQUIRED for create_application] (candidate ID)
- `source_id`: integer [OPTIONAL] (source ID)
- `referrer`: object [OPTIONAL] (referrer information)

## Example Request Bodies

**Create Candidate:**
```json
{"first_name": "Jane", "last_name": "Doe", "email_addresses": [{"value": "jane@example.com", "type": "personal"}]}
```

**Create Application:**
```json
{"job_id": 123, "candidate_id": 456, "source_id": 789}
```
