---
name: icims-ats
description: Manage candidates and jobs via iCIMS. Use when the user mentions icims,
  ats, candidate, job, applicant, recruiting.
version: 1.0.0
skill_type: external
base_url_env: ICIMS_BASE_URL
auth_env_var: ICIMS_API_TOKEN
auth_type: bearer
triggers:
  - icims
  - ats
  - candidate
  - job
  - applicant
  - recruiting
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ICIMS_BASE_URL and ICIMS_API_TOKEN environment variables.
---

# Icims-Ats

Manage candidates and jobs via iCIMS. Use when the user mentions icims, ats, candidate, job, applicant, recruiting.

## API Endpoints

- **GET** `/applicantworkflows` - Search applicant workflows
- **GET** `/people/{personId}` - Get person
- **POST** `/people` - Create person
- **GET** `/jobs` - Search jobs
- **GET** `/jobs/{jobId}` - Get job
- **POST** `/jobs` - Create job
- **GET** `/applicantworkflows/{id}` - Get workflow
- **POST** `/applicantworkflows` - Create workflow
- **DELETE** `/people/{personId}` - Delete a person
- **DELETE** `/jobs/{jobId}` - Delete a job

## Actions

- list: Search applicant workflows (GET /applicantworkflows)
- get_by_id: Get person (GET /people/{personId})
- create: Create person (POST /people)
- list_jobs: Search jobs (GET /jobs)
- get_by_id_jobs: Get job (GET /jobs/{jobId})
- create_jobs: Create job (POST /jobs)
- get_by_id_applicantworkflows: Get workflow (GET /applicantworkflows/{id})
- create_applicantworkflows: Create workflow (POST /applicantworkflows)
- delete: Delete a person (DELETE /people/{personId})
- delete_jobs: Delete a job (DELETE /jobs/{jobId})

## Fields

- `firstname`: string [REQUIRED for create_person]
- `lastname`: string [REQUIRED for create_person]
- `email`: string [OPTIONAL]

## Example Request Bodies

**Create Person:**
```json
{"firstname": "John", "lastname": "Smith", "email": "john.smith@example.com"}
```

**Create Job:**
```json
{"title": "Software Engineer", "department": "Engineering", "location": "Remote"}
```
