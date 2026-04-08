---
name: breezyhr-ats
description: Manage candidates, positions, and pipelines in Breezy HR ATS. Use when
  the user mentions breezy hr, breezyhr, breezy candidate, breezy position, breezy
  hiring.
version: 1.0.0
skill_type: external
base_url_env: BREEZYHR_BASE_URL
auth_env_var: BREEZYHR_API_TOKEN
auth_type: bearer
triggers:
  - breezy hr
  - breezyhr
  - breezy candidate
  - breezy position
  - breezy hiring
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BREEZYHR_BASE_URL and BREEZYHR_API_TOKEN environment variables.
---

# Breezyhr-Ats

Manage candidates, positions, and pipelines in Breezy HR ATS. Use when the user mentions breezy hr, breezyhr, breezy candidate, breezy position, breezy hiring.

## API Endpoints

- **GET** `/v3/company/{company_id}/positions` - List positions
- **POST** `/v3/company/{company_id}/positions` - Create a position
- **GET** `/v3/company/{company_id}/position/{position_id}` - Get a position by ID
- **PUT** `/v3/company/{company_id}/position/{position_id}` - Update a position
- **GET** `/v3/company/{company_id}/position/{position_id}/candidates` - List candidates for position
- **POST** `/v3/company/{company_id}/position/{position_id}/candidates` - Create a candidate
- **GET** `/v3/company/{company_id}/position/{position_id}/candidate/{candidate_id}` - Get a candidate
- **PUT** `/v3/company/{company_id}/position/{position_id}/candidate/{candidate_id}` - Update a candidate
- **GET** `/v3/company/{company_id}/position/{position_id}/pipeline` - Get position pipeline stages

## Actions

- list: List positions (GET /v3/company/{company_id}/positions)
- create: Create a position (POST /v3/company/{company_id}/positions)
- get_by_id: Get a position by ID (GET /v3/company/{company_id}/position/{position_id})
- update: Update a position (PUT /v3/company/{company_id}/position/{position_id})
- list_candidates: List candidates for position (GET /v3/company/{company_id}/position/{position_id}/candidates)
- create_candidates: Create a candidate (POST /v3/company/{company_id}/position/{position_id}/candidates)
- get_by_id_candidate: Get a candidate (GET /v3/company/{company_id}/position/{position_id}/candidate/{candidate_id})
- update_candidate: Update a candidate (PUT /v3/company/{company_id}/position/{position_id}/candidate/{candidate_id})
- list_pipeline: Get position pipeline stages (GET /v3/company/{company_id}/position/{position_id}/pipeline)

## Fields

- `company_id`: string [REQUIRED] (company ID)
- `position_id`: string [REQUIRED for get_position, update_position, list_candidates, create_candidate, list_pipeline] (position ID)
- `candidate_id`: string [REQUIRED for get_candidate, update_candidate] (candidate ID)
- `name`: string [REQUIRED for create_candidate, create_position] (name)
- `email_address`: string [OPTIONAL] (email address)
- `phone_number`: string [OPTIONAL] (phone number)
- `headline`: string [OPTIONAL] (candidate headline)
- `summary`: string [OPTIONAL] (candidate summary)
- `stage_id`: string [OPTIONAL] (pipeline stage ID)
- `description`: string [OPTIONAL] (position description)

## Example Request Bodies

**Create Candidate:**
```json
{"name": "Jane Doe", "email_address": "jane@example.com", "phone_number": "+1234567890", "headline": "Senior Engineer"}
```

**Create Position:**
```json
{"name": "Senior Software Engineer", "description": "Build scalable systems", "type": "full-time"}
```
