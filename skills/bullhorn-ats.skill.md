---
name: bullhorn-ats
description: 'Manage candidates, jobs, and placements via Bullhorn ATS. Use when the
  user mentions bullhorn, ats, candidate, job, placement, staffing, recruiting.

  '
version: 1.0.0
skill_type: external
base_url_env: BULLHORN_BASE_URL
auth_env_var: BULLHORN_API_TOKEN
auth_type: bearer
triggers:
  - bullhorn
  - ats
  - candidate
  - job
  - placement
  - staffing
  - recruiting
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BULLHORN_BASE_URL and BULLHORN_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Bullhorn-Ats

Manage candidates, jobs, and placements via Bullhorn ATS. Use when the user mentions bullhorn, ats, candidate, job, placement, staffing, recruiting.


## API Endpoints

- **GET** `/entity/Candidate` - List candidates
- **PUT** `/entity/Candidate` - Create a candidate
- **GET** `/entity/Candidate/{id}` - Get candidate by ID
- **POST** `/entity/Candidate/{id}` - Update a candidate
- **GET** `/entity/JobOrder` - List job orders
- **PUT** `/entity/JobOrder` - Create a job order
- **GET** `/entity/Placement` - List placements
- **GET** `/search/Candidate` - Search candidates

## Actions

- list: List candidates (GET /entity/Candidate)
- put_candidate: Create a candidate (PUT /entity/Candidate)
- get_by_id: Get candidate by ID (GET /entity/Candidate/{id})
- add_candidate: Update a candidate (POST /entity/Candidate/{id})
- list_job_orders: List job orders (GET /entity/JobOrder)
- put_joborder: Create a job order (PUT /entity/JobOrder)
- list_placements: List placements (GET /entity/Placement)
- search_candidates: Search candidates (GET /search/Candidate)

## Fields

- `firstName`: string [REQUIRED for create] — First display name
- `lastName`: string [REQUIRED for create] — Last display name
- `name`: string [OPTIONAL] — Display name
- `status`: string [OPTIONAL] — Current status

## Example Request Bodies

**Create Candidate:**
```json
{"firstName": "Alice", "lastName": "Smith", "name": "Alice Smith", "status": "Active"}
```

**Update Candidate:**
```json
{"status": "Placed", "name": "Alice Johnson"}

## Response

**Candidate object:**
- `id`: string — Unique candidate identifier
- `name`: string — Candidate name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 404 | Resource not found — check the ID or identifier |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
