---
name: ashby-ats
description: Comprehensive integration for Ashby ATS (Candidates, Jobs, Applications,
  Interview Schedules, Offers, etc.). Use when the user mentions ashby, ashby candidate,
  ashby job, ashby application, ashby interview, ashby offer, ashby hiring, ashby
  department.
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
- create_candidate_info: Get candidate details by ID (POST /candidate.info)
- create_candidate_list: List candidates (paginated) (POST /candidate.list)
- search: Search by name or email (POST /candidate.search)
- create_candidate_update: Update candidate details (POST /candidate.update)
- create_candidate_createnote: Add a note to a candidate (POST /candidate.createNote)
- create_candidate_listnotes: List notes for a candidate (POST /candidate.listNotes)
- create_candidate_uploadresume: Upload and parse a resume (POST /candidate.uploadResume)
- create_candidate_uploadfile: Upload a general file (POST /candidate.uploadFile)
- create_candidate_addtag: Attach a tag to a candidate (POST /candidate.addTag)
- create_candidate_removetag: Detach a tag from a candidate (POST /candidate.removeTag)
- create_candidate_anonymize: Anonymize candidate PII (POST /candidate.anonymize)
- create_job_create: Create a new job (POST /job.create)
- create_job_info: Get job details by ID (POST /job.info)
- create_job_list: List jobs (paginated) (POST /job.list)

## Fields

### Primary Identifiers
- `candidateId`: string [REQUIRED for info/update/note] (Unique candidate ID)
- `jobId`: string [REQUIRED for info/update/apply] (Unique job ID)
- `applicationId`: string [REQUIRED for info/stage/transfer] (Unique application ID)
- `interviewStageId`: string [REQUIRED for changeStage] (Target stage ID)
- `offerId`: string [REQUIRED for info/approve] (Unique offer ID)

### Candidate Data
- `name`: string [REQUIRED for create] (Full name)
- `email`: string [OPTIONAL] (Email address)
- `phoneNumber`: string [OPTIONAL] (Contact number)
- `linkedInUrl`: string [OPTIONAL] (LinkedIn URL)
- `resumeHandle`: string [REQUIRED for uploadResume] (Handle from file.createFileUploadHandle)
- `noteText`: string [REQUIRED for createNote] (Content of the note)

### Job Data
- `title`: string [REQUIRED for create] (Job title)
- `departmentId`: string [OPTIONAL] (Department ID)
- `locationId`: string [OPTIONAL] (Location ID)
- `status`: string (e.g., "Draft", "Open", "Closed", "Archived")

### Custom Fields
- `objectId`: string [REQUIRED] (ID of the object being updated)
- `customFieldId`: string [REQUIRED] (ID of the custom field)
- `value`: any [REQUIRED] (Value to set)

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
