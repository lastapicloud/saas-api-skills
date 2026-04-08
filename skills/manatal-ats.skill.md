---
name: manatal-ats
description: Manage candidates and jobs via Manatal ATS. Use when the user mentions
  manatal, ats, candidate, job, recruiting, applicant.
version: 1.0.0
skill_type: external
base_url_env: MANATAL_BASE_URL
auth_env_var: MANATAL_API_TOKEN
auth_type: bearer
triggers:
  - manatal
  - ats
  - candidate
  - job
  - recruiting
  - applicant
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MANATAL_BASE_URL and MANATAL_API_TOKEN environment variables.
---

# Manatal-Ats

Manage candidates and jobs via Manatal ATS. Use when the user mentions manatal, ats, candidate, job, recruiting, applicant.

## API Endpoints

- **GET** `/open/v3/candidates/` - List candidates
- **POST** `/open/v3/candidates/` - Create candidate
- **GET** `/open/v3/candidates/{id}/` - Get candidate
- **PATCH** `/open/v3/candidates/{id}/` - Update candidate
- **DELETE** `/open/v3/candidates/{id}/` - Delete candidate
- **GET** `/open/v3/jobs/` - List jobs
- **POST** `/open/v3/jobs/` - Create job
- **GET** `/open/v3/stages/` - List stages

## Actions

- list: List candidates (GET /open/v3/candidates/)
- create: Create candidate (POST /open/v3/candidates/)
- get_by_id: Get candidate (GET /open/v3/candidates/{id}/)
- update: Update candidate (PATCH /open/v3/candidates/{id}/)
- delete: Delete candidate (DELETE /open/v3/candidates/{id}/)
- list_jobs: List jobs (GET /open/v3/jobs/)
- create_jobs: Create job (POST /open/v3/jobs/)
- list_stages: List stages (GET /open/v3/stages/)

## Fields

- `first_name`: string [REQUIRED for create]
- `last_name`: string [REQUIRED for create]
- `email`: string [OPTIONAL]

## Example Request Bodies

**Create Candidate:**
```json
{"first_name": "Carlos", "last_name": "Rivera", "email": "carlos.rivera@example.com"}
```

**Create Job:**
```json
{"position_name": "Backend Developer", "department": "Engineering", "status": "open"}
```
