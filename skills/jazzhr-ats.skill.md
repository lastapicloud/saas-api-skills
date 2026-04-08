---
name: jazzhr-ats
description: Manage applicants, jobs, and hiring workflows in JazzHR ATS. Use when
  the user mentions jazzhr, jazz hr, jazzhr applicant, jazzhr job, jazzhr hiring.
version: 1.0.0
skill_type: external
base_url_env: JAZZHR_BASE_URL
auth_env_var: JAZZHR_API_KEY
auth_type: header
triggers:
  - jazzhr
  - jazz hr
  - jazzhr applicant
  - jazzhr job
  - jazzhr hiring
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires JAZZHR_BASE_URL and JAZZHR_API_KEY environment variables.
---

# Jazzhr-Ats

Manage applicants, jobs, and hiring workflows in JazzHR ATS. Use when the user mentions jazzhr, jazz hr, jazzhr applicant, jazzhr job, jazzhr hiring.

## API Endpoints

- **GET** `/applicants` - List applicants
- **GET** `/applicants/{id}` - Get an applicant by ID
- **POST** `/applicants` - Create an applicant
- **GET** `/jobs` - List jobs
- **GET** `/jobs/{id}` - Get a job by ID
- **POST** `/jobs` - Create a job
- **GET** `/activities` - List activities
- **GET** `/categories` - List job categories
- **GET** `/hires` - List hires
- **GET** `/applicants2jobs/{id}` - Get applicant-to-job mapping
- **DELETE** `/applicants/{id}` - Delete an applicant
- **DELETE** `/jobs/{id}` - Delete a job

## Actions

- list: List applicants (GET /applicants)
- get_by_id: Get an applicant by ID (GET /applicants/{id})
- create: Create an applicant (POST /applicants)
- list_jobs: List jobs (GET /jobs)
- get_by_id_jobs: Get a job by ID (GET /jobs/{id})
- create_jobs: Create a job (POST /jobs)
- list_activities: List activities (GET /activities)
- list_categories: List job categories (GET /categories)
- list_hires: List hires (GET /hires)
- get_by_id_applicants2jobs: Get applicant-to-job mapping (GET /applicants2jobs/{id})
- delete: Delete an applicant (DELETE /applicants/{id})
- delete_jobs: Delete a job (DELETE /jobs/{id})

## Fields

- `id`: string [REQUIRED for get_applicant, get_job, get_applicant_job] (record ID)
- `first_name`: string [REQUIRED for create_applicant] (first name)
- `last_name`: string [REQUIRED for create_applicant] (last name)
- `email`: string [OPTIONAL] (email address)
- `phone`: string [OPTIONAL] (phone number)
- `job_id`: string [REQUIRED for create_applicant] (job ID to apply to)
- `title`: string [REQUIRED for create_job] (job title)
- `description`: string [OPTIONAL] (job description)
- `city`: string [OPTIONAL] (job location city)
- `state`: string [OPTIONAL] (job location state)

## Example Request Bodies

**Create Applicant:**
```json
{"first_name": "Jane", "last_name": "Doe", "email": "jane@example.com", "job_id": "job_abc123"}
```

**Create Job:**
```json
{"title": "Senior Software Engineer", "description": "Build scalable systems", "city": "San Francisco", "state": "CA"}
```
