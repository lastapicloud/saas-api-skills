---
name: bullhorn-ats
description: Manage candidates, jobs, and placements via Bullhorn ATS. Use when the
  user mentions bullhorn, ats, candidate, job, placement, staffing, recruiting.
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
- list_joborder: List job orders (GET /entity/JobOrder)
- put_joborder: Create a job order (PUT /entity/JobOrder)
- list_placement: List placements (GET /entity/Placement)
- list_candidate: Search candidates (GET /search/Candidate)

## Fields

- `firstName`: string [REQUIRED for create]
- `lastName`: string [REQUIRED for create]
- `name`: string [OPTIONAL]
- `status`: string [OPTIONAL]

## Example Request Bodies

**Create Candidate:**
```json
{"firstName": "Alice", "lastName": "Smith", "name": "Alice Smith", "status": "Active"}
```

**Update Candidate:**
```json
{"status": "Placed", "name": "Alice Johnson"}
