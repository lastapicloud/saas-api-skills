---
name: jobvite-ats
description: Manage candidates and jobs via Jobvite. Use when the user mentions jobvite,
  ats, candidate, job, requisition, recruiting.
version: 1.0.0
skill_type: external
base_url_env: JOBVITE_BASE_URL
auth_env_var: JOBVITE_API_KEY
auth_user_env: JOBVITE_API_SECRET
auth_type: header
triggers:
  - jobvite
  - ats
  - candidate
  - job
  - requisition
  - recruiting
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires JOBVITE_BASE_URL and JOBVITE_API_KEY environment variables.
---

# Jobvite-Ats

Manage candidates and jobs via Jobvite. Use when the user mentions jobvite, ats, candidate, job, requisition, recruiting.

## API Endpoints

- **GET** `/api/v2/candidate` - List candidates
- **POST** `/api/v2/candidate` - Create candidate
- **GET** `/api/v2/candidate/{candidateId}` - Get candidate
- **PUT** `/api/v2/candidate/{candidateId}` - Update candidate
- **GET** `/api/v2/job` - List jobs
- **GET** `/api/v2/job/{jobId}` - Get job
- **GET** `/api/v2/application` - List applications
- **POST** `/api/v2/application` - Create application

## Actions

- list: List candidates (GET /api/v2/candidate)
- create: Create candidate (POST /api/v2/candidate)
- get_by_id: Get candidate (GET /api/v2/candidate/{candidateId})
- update: Update candidate (PUT /api/v2/candidate/{candidateId})
- list_job: List jobs (GET /api/v2/job)
- get_by_id_job: Get job (GET /api/v2/job/{jobId})
- list_application: List applications (GET /api/v2/application)
- create_application: Create application (POST /api/v2/application)

## Fields

- `firstName`: string [REQUIRED for create]
- `lastName`: string [REQUIRED for create]
- `email`: string [OPTIONAL]

## Example Request Bodies

**Create Candidate:**
```json
{"firstName": "Sarah", "lastName": "Johnson", "email": "sarah.johnson@example.com"}
```

**Create Application:**
```json
{"candidateId": "cand-abc123", "jobId": "job-xyz789", "source": "LinkedIn"}
```
