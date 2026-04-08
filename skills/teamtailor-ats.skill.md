---
name: teamtailor-ats
description: Manage Teamtailor ATS candidates, jobs, and departments. Use when the
  user mentions teamtailor, candidate, job, ATS, hiring, department.
version: 1.0.0
skill_type: external
base_url_env: TEAMTAILOR_BASE_URL
auth_env_var: TEAMTAILOR_API_TOKEN
auth_type: bearer
triggers:
  - teamtailor
  - candidate
  - job
  - ATS
  - hiring
  - department
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TEAMTAILOR_BASE_URL and TEAMTAILOR_API_TOKEN environment variables.
---

# Teamtailor-Ats

Manage Teamtailor ATS candidates, jobs, and departments. Use when the user mentions teamtailor, candidate, job, ATS, hiring, department.

## API Endpoints

- **GET** `/v1/candidates` - List candidates
- **GET** `/v1/candidates/{candidateId}` - Get a candidate
- **POST** `/v1/candidates` - Create a candidate
- **PATCH** `/v1/candidates/{candidateId}` - Update a candidate
- **DELETE** `/v1/candidates/{candidateId}` - Delete a candidate
- **GET** `/v1/jobs` - List jobs
- **POST** `/v1/jobs` - Create a job
- **GET** `/v1/departments` - List departments
- **GET** `/v1/stages` - List stages
- **GET** `/v1/job-applications` - List job applications

## Actions

- list: List candidates (GET /v1/candidates)
- get_by_id: Get a candidate (GET /v1/candidates/{candidateId})
- create: Create a candidate (POST /v1/candidates)
- update: Update a candidate (PATCH /v1/candidates/{candidateId})
- delete: Delete a candidate (DELETE /v1/candidates/{candidateId})
- list_jobs: List jobs (GET /v1/jobs)
- create_jobs: Create a job (POST /v1/jobs)
- list_departments: List departments (GET /v1/departments)
- list_stages: List stages (GET /v1/stages)
- list_job_applications: List job applications (GET /v1/job-applications)

## Fields

- `first-name`: string [REQUIRED for create]
- `last-name`: string [REQUIRED for create]
- `email`: string [REQUIRED for create]
- `phone`: string [OPTIONAL]
- `connected`: boolean [OPTIONAL]

## Example Request Bodies

**Create Candidate:**
```json
{"first-name": "Alice", "last-name": "Johnson", "email": "alice@example.com", "phone": "+15551234567"}
```

**Update Candidate:**
```json
{"first-name": "Alice", "last-name": "Johnson-Smith", "connected": true}
```
