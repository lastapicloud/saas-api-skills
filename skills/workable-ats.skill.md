---
name: workable-ats
description: Manage candidates, jobs, and stages in Workable ATS. Use when the user
  mentions workable, workable candidate, workable job, workable hiring.
version: 1.0.0
skill_type: external
base_url_env: WORKABLE_BASE_URL
auth_env_var: WORKABLE_API_TOKEN
auth_type: bearer
triggers:
  - workable
  - workable candidate
  - workable job
  - workable hiring
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires WORKABLE_BASE_URL and WORKABLE_API_TOKEN environment variables.
---

# Workable-Ats

Manage candidates, jobs, and stages in Workable ATS. Use when the user mentions workable, workable candidate, workable job, workable hiring.

## API Endpoints

- **GET** `/spi/v3/jobs` - List jobs
- **GET** `/spi/v3/jobs/{shortcode}` - Get a job by shortcode
- **POST** `/spi/v3/jobs` - Create a job
- **GET** `/spi/v3/jobs/{shortcode}/candidates` - List candidates for a job
- **POST** `/spi/v3/jobs/{shortcode}/candidates` - Create a candidate for a job
- **GET** `/spi/v3/candidates/{id}` - Get a candidate by ID
- **PUT** `/spi/v3/candidates/{id}/move` - Move a candidate to a stage
- **PUT** `/spi/v3/candidates/{id}/disqualify` - Disqualify a candidate
- **GET** `/spi/v3/stages` - List hiring stages
- **GET** `/spi/v3/members` - List team members

## Actions

- list: List jobs (GET /spi/v3/jobs)
- get_by_id: Get a job by shortcode (GET /spi/v3/jobs/{shortcode})
- create: Create a job (POST /spi/v3/jobs)
- list_candidates: List candidates for a job (GET /spi/v3/jobs/{shortcode}/candidates)
- create_candidates: Create a candidate for a job (POST /spi/v3/jobs/{shortcode}/candidates)
- get_by_id_candidates: Get a candidate by ID (GET /spi/v3/candidates/{id})
- put_move: Move a candidate to a stage (PUT /spi/v3/candidates/{id}/move)
- put_disqualify: Disqualify a candidate (PUT /spi/v3/candidates/{id}/disqualify)
- list_stages: List hiring stages (GET /spi/v3/stages)
- list_members: List team members (GET /spi/v3/members)

## Fields

- `id`: string [REQUIRED for get_candidate, move_candidate, disqualify_candidate] (candidate ID)
- `shortcode`: string [REQUIRED for get_job, list_candidates, create_candidate] (job shortcode)
- `name`: string [REQUIRED for create_candidate] (candidate full name)
- `firstname`: string [OPTIONAL] (first name)
- `lastname`: string [OPTIONAL] (last name)
- `email`: string [OPTIONAL] (email address)
- `headline`: string [OPTIONAL] (candidate headline)
- `summary`: string [OPTIONAL] (candidate summary)
- `stage`: string [REQUIRED for move_candidate] (stage slug to move to)
- `title`: string [REQUIRED for create_job] (job title)

## Example Request Bodies

**Create Candidate:**
```json
{"name": "Jane Doe", "firstname": "Jane", "lastname": "Doe", "email": "jane@example.com", "headline": "Senior Engineer"}
```

**Move Candidate:**
```json
{"stage": "interview"}
```
