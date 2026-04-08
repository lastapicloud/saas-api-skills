---
name: smartrecruiters-ats
description: Manage candidates, jobs, and applications in SmartRecruiters ATS. Use
  when the user mentions smartrecruiters, smart recruiters, smartrecruiters candidate,
  smartrecruiters job, smartrecruiters application.
version: 1.0.0
skill_type: external
base_url_env: SMARTRECRUITERS_BASE_URL
auth_env_var: SMARTRECRUITERS_API_KEY
auth_type: header
triggers:
  - smartrecruiters
  - smart recruiters
  - smartrecruiters candidate
  - smartrecruiters job
  - smartrecruiters application
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SMARTRECRUITERS_BASE_URL and SMARTRECRUITERS_API_KEY environment
  variables.
---

# Smartrecruiters-Ats

Manage candidates, jobs, and applications in SmartRecruiters ATS. Use when the user mentions smartrecruiters, smart recruiters, smartrecruiters candidate, smartrecruiters job, smartrecruiters application.

## API Endpoints

- **GET** `/jobs` - List jobs
- **POST** `/jobs` - Create a job
- **GET** `/jobs/{id}` - Get a job by ID
- **PATCH** `/jobs/{id}` - Update a job
- **GET** `/jobs/{id}/candidates` - List candidates for a job
- **POST** `/jobs/{id}/candidates` - Create a candidate for a job
- **GET** `/candidates/{id}` - Get a candidate by ID
- **GET** `/jobs/{id}/candidates/{candidateId}/screening-answers` - Get screening answers
- **GET** `/postings` - List job postings
- **GET** `/offer-statuses` - List offer statuses

## Actions

- list: List jobs (GET /jobs)
- create: Create a job (POST /jobs)
- get_by_id: Get a job by ID (GET /jobs/{id})
- update: Update a job (PATCH /jobs/{id})
- list_candidates: List candidates for a job (GET /jobs/{id}/candidates)
- create_candidates: Create a candidate for a job (POST /jobs/{id}/candidates)
- get_by_id_candidates: Get a candidate by ID (GET /candidates/{id})
- list_screening_answers: Get screening answers (GET /jobs/{id}/candidates/{candidateId}/screening-answers)
- list_postings: List job postings (GET /postings)
- list_offer_statuses: List offer statuses (GET /offer-statuses)

## Fields

- `id`: string [REQUIRED for get_job, update_job, list_candidates, create_candidate, get_candidate] (record ID)
- `candidateId`: string [REQUIRED for get_screening_answers] (candidate ID)
- `title`: string [REQUIRED for create_job] (job title)
- `department`: object [OPTIONAL] (department with id and label fields)
- `location`: object [OPTIONAL] (location with city, country fields)
- `firstName`: string [REQUIRED for create_candidate] (first name)
- `lastName`: string [REQUIRED for create_candidate] (last name)
- `email`: string [OPTIONAL] (candidate email)
- `phoneNumber`: string [OPTIONAL] (phone number)
- `web`: object [OPTIONAL] (URLs like linkedin, portfolio)

## Example Request Bodies

**Create Job:**
```json
{"title": "Senior Software Engineer", "department": {"id": "dept_123"}, "location": {"city": "San Francisco", "country": "US"}}
```

**Create Candidate:**
```json
{"firstName": "Jane", "lastName": "Doe", "email": "jane@example.com", "phoneNumber": "+1234567890"}
```
