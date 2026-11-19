---
name: sap-successfactors-hr
description: 'Manage employees and HR data via SAP SuccessFactors. Use when the user
  mentions sap, successfactors, hr, employee, performance, learning.

  '
version: 1.0.0
skill_type: external
base_url_env: SAP_SUCCESSFACTORS_BASE_URL
auth_env_var: SAP_SUCCESSFACTORS_API_TOKEN
auth_type: bearer
triggers:
  - sap
  - successfactors
  - hr
  - employee
  - performance
  - learning
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SAP_SUCCESSFACTORS_BASE_URL and SAP_SUCCESSFACTORS_API_TOKEN
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Sap-Successfactors-Hr

Manage employees and HR data via SAP SuccessFactors. Use when the user mentions sap, successfactors, hr, employee, performance, learning.


## API Endpoints

- **GET** `/odata/v2/JobRequisition(1197)` - JobRequisition By Id
- **GET** `/odata/v2/JobApplication` - Job Applicant
- **GET** `/odata/v2/JobApplication` - Job Applicant Copy
- **GET** `/odata/v2/JobApplication` - Job Applicant Copy 2
- **GET** `/odata/v2/Candidate` - Candidate
- **GET** `/odata/v2/JobRequisition(631)/jobProfile` - Job Profile
- **GET** `/odata/v2/Candidate(578)/resume` - Candidate Resume
- **GET** `/odata/v2/JobRequisition(1176L)/jobProfile` - Job Profile Responsibility
- **GET** `/odata/v2/JobRequisition(1197L)/jobApplications` - https://api55.sapsf.eu/odata/v2/JobRequisition(1197L)/jobApplications

## Actions

- list: JobRequisition By Id (GET /odata/v2/JobRequisition(1197))
- get_job_applicant: Job Applicant (GET /odata/v2/JobApplication)
- get_job_applicant_copy: Job Applicant Copy (GET /odata/v2/JobApplication)
- list_jobapplication: Job Applicant Copy 2 (GET /odata/v2/JobApplication)
- get_candidate: Candidate (GET /odata/v2/Candidate)
- get_job_profile: Job Profile (GET /odata/v2/JobRequisition(631)/jobProfile)
- get_candidate_resume: Candidate Resume (GET /odata/v2/Candidate(578)/resume)
- get_job_profile_responsibility: Job Profile Responsibility (GET /odata/v2/JobRequisition(1176L)/jobProfile)
- list_jobapplications: https://api55.sapsf.eu/odata/v2/JobRequisition(1197L)/jobApplications (GET /odata/v2/JobRequisition(1197L)/jobApplications)

## Fields

- `$filter`: string [OPTIONAL]
- `$select`: string [OPTIONAL]
- `$top`: integer [OPTIONAL]

## Example Request Bodies

**Create Time Off:**
```json
{"userId": "EMP001", "timeType": "VACATION", "startDate": "2026-04-01", "endDate": "2026-04-05"}
```

**List Users with Filter:**
```json
{"$filter": "department eq 'Engineering'", "$select": "userId,firstName,lastName", "$top": 50}

## Response

**Jobapplication object:**
- `id`: string — Unique jobapplication identifier
- `name`: string — Jobapplication name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 404 | Resource not found — check the ID or identifier |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
