---
name: ashby-ats
description: 'Comprehensive integration for Ashby ATS (Candidates, Jobs, Applications,
  Interview Schedules, Offers, etc.). Use when the user mentions ashby, ashby candidate,
  ashby job, ashby application, ashby interview, ashby offer, ashby hiring, ashby
  department.

  '
version: 1.0.0
skill_type: external
base_url_env: ASHBY_BASE_URL
auth_env_var: ASHBY_API_KEY
auth_type: basic
triggers:
  - ashby
  - ashby candidate
  - ashby job
  - ashby application
  - ashby interview
  - ashby offer
  - ashby hiring
  - ashby department
license: Apache-2.0
metadata:
  author: lastapi
  version: 2.0.0
compatibility: Requires ASHBY_BASE_URL and ASHBY_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Ashby-Ats

Comprehensive integration for Ashby ATS (Candidates, Jobs, Applications, Interview Schedules, Offers, etc.). Use when the user mentions ashby, ashby candidate, ashby job, ashby application, ashby interview, ashby offer, ashby hiring, ashby department.


## API Endpoints

- **POST** `/candidate.create` - Create a candidate
- **POST** `/candidate.info` - Get candidate details by ID
- **POST** `/candidate.list` - List candidates (paginated)
- **POST** `/candidate.search` - Search by name or email
- **POST** `/candidate.update` - Update candidate details
- **POST** `/candidate.createNote` - Add a note to a candidate
- **POST** `/candidate.listNotes` - List notes for a candidate
- **POST** `/candidate.uploadResume` - Upload and parse a resume
- **POST** `/candidate.uploadFile` - Upload a general file
- **POST** `/candidate.addTag` - Attach a tag to a candidate
- **POST** `/candidate.removeTag` - Detach a tag from a candidate
- **POST** `/candidate.anonymize` - Anonymize candidate PII
- **POST** `/job.create` - Create a new job
- **POST** `/job.info` - Get job details by ID
- **POST** `/job.list` - List jobs (paginated)

## Actions

- create: Create a candidate (POST /candidate.create)
- get_candidate_details_id: Get candidate details by ID (POST /candidate.info)
- list_candidates_paginated: List candidates (paginated) (POST /candidate.list)
- search: Search by name or email (POST /candidate.search)
- update_candidate_details: Update candidate details (POST /candidate.update)
- add_note_candidate: Add a note to a candidate (POST /candidate.createNote)
- list_notes_candidate: List notes for a candidate (POST /candidate.listNotes)
- upload_parse_resume: Upload and parse a resume (POST /candidate.uploadResume)
- upload_general_file: Upload a general file (POST /candidate.uploadFile)
- create_attach_tag_candidate: Attach a tag to a candidate (POST /candidate.addTag)
- create_detach_tag_candidate: Detach a tag from a candidate (POST /candidate.removeTag)
- create_anonymize_candidate_pii: Anonymize candidate PII (POST /candidate.anonymize)
- create_new_job: Create a new job (POST /job.create)
- get_job_details_id: Get job details by ID (POST /job.info)
- list_jobs_paginated: List jobs (paginated) (POST /job.list)

## Fields

### Primary Identifiers
- `candidateId`: string [REQUIRED for info/update/note] (Unique candidate ID) — Candate unique identifier
- `jobId`: string [REQUIRED for info/update/apply] (Unique job ID) — Job unique identifier
- `applicationId`: string [REQUIRED for info/stage/transfer] (Unique application ID) — Application unique identifier
- `interviewStageId`: string [REQUIRED for changeStage] (Target stage ID) — Interviewstage unique identifier
- `offerId`: string [REQUIRED for info/approve] (Unique offer ID) — Offer unique identifier

### Candidate Data
- `name`: string [REQUIRED for create] (Full name) — Display name
- `email`: string [OPTIONAL] (Email address) — Email address
- `phoneNumber`: string [OPTIONAL] (Contact number) — Phonenumber
- `linkedInUrl`: string [OPTIONAL] (LinkedIn URL) — Linkedin url
- `resumeHandle`: string [REQUIRED for uploadResume] (Handle from file.createFileUploadHandle) — Resumehandle
- `noteText`: string [REQUIRED for createNote] (Content of the note) — Note text content

### Job Data
- `title`: string [REQUIRED for create] (Job title) — Title or heading
- `departmentId`: string [OPTIONAL] (Department ID) — Department unique identifier
- `locationId`: string [OPTIONAL] (Location ID) — Location unique identifier
- `status`: string (e.g., "Draft", "Open", "Closed", "Archived") — Current status

### Custom Fields
- `objectId`: string [REQUIRED] (ID of the object being updated) — Object unique identifier
- `customFieldId`: string [REQUIRED] (ID of the custom field) — Customfield unique identifier
- `value`: any [REQUIRED] (Value to set) — Value

## Example Request Bodies

**Create Candidate:**
```json
{
  "name": "Alex Smith",
  "email": "alex@smith.com",
  "phoneNumber": "+1-555-0199",
  "linkedInUrl": "https://linkedin.com/in/alexsmith",
  "sourceId": "source_direct"
}
```

**Move Application Stage:**
```json
{
  "applicationId": "app_123",
  "interviewStageId": "stage_recruiter_screen"
}
```

**Set Custom Field (Salary Range):**
```json
{
  "objectId": "job_456",
  "customFieldId": "field_salary_max",
  "value": 150000
}
```

**Create Interview Schedule:**
```json
{
  "applicationId": "app_123",
  "interviewPlanId": "plan_789",
  "slots": [
    {"startTime": "2026-04-01T10:00:00Z", "endTime": "2026-04-01T11:00:00Z"}
  ]
}
```

## Response

**Candidate.Create object:**
- `id`: string — Unique candidate.create identifier
- `name`: string — Candidate.Create name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)


**Required fields reference:**
```json
{
  "candidateId": "example_candidateId",
  "jobId": "example_jobId",
  "offerId": "example_offerId",
  "resumeHandle": "example_resumeHandle",
  "noteText": "example_noteText",
  "title": "example_title"
}
```


**Required fields reference:**
```json
{
  "candidateId": "example_candidateId",
  "jobId": "example_jobId",
  "offerId": "example_offerId",
  "resumeHandle": "example_resumeHandle",
  "noteText": "example_noteText",
  "title": "example_title"
}
```

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
