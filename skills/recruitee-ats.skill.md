---
name: recruitee-ats
description: Manage candidates, offers, and job pipelines in Recruitee (Tellent) ATS.
  Use when the user mentions recruitee, tellent, recruitee candidate, recruitee offer,
  recruitee pipeline.
version: 1.0.0
skill_type: external
base_url_env: RECRUITEE_BASE_URL
auth_env_var: RECRUITEE_API_TOKEN
auth_type: bearer
triggers:
  - recruitee
  - tellent
  - recruitee candidate
  - recruitee offer
  - recruitee pipeline
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires RECRUITEE_BASE_URL and RECRUITEE_API_TOKEN environment variables.
---

# Recruitee-Ats

Manage candidates, offers, and job pipelines in Recruitee (Tellent) ATS. Use when the user mentions recruitee, tellent, recruitee candidate, recruitee offer, recruitee pipeline.

## API Endpoints

- **GET** `/c/{company_id}/candidates` - List candidates
- **POST** `/c/{company_id}/candidates` - Create a candidate
- **GET** `/c/{company_id}/candidates/{id}` - Get a candidate by ID
- **PATCH** `/c/{company_id}/candidates/{id}` - Update a candidate
- **DELETE** `/c/{company_id}/candidates/{id}` - Delete a candidate
- **GET** `/c/{company_id}/offers` - List job offers (postings)
- **GET** `/c/{company_id}/offers/{id}` - Get a job offer by ID
- **POST** `/c/{company_id}/offers` - Create a job offer
- **GET** `/c/{company_id}/pipeline_templates` - List pipeline templates
- **GET** `/c/{company_id}/departments` - List departments

## Actions

- list: List candidates (GET /c/{company_id}/candidates)
- create: Create a candidate (POST /c/{company_id}/candidates)
- get_by_id: Get a candidate by ID (GET /c/{company_id}/candidates/{id})
- update: Update a candidate (PATCH /c/{company_id}/candidates/{id})
- delete: Delete a candidate (DELETE /c/{company_id}/candidates/{id})
- list_offers: List job offers (postings) (GET /c/{company_id}/offers)
- get_by_id_offers: Get a job offer by ID (GET /c/{company_id}/offers/{id})
- create_offers: Create a job offer (POST /c/{company_id}/offers)
- list_pipeline_templates: List pipeline templates (GET /c/{company_id}/pipeline_templates)
- list_departments: List departments (GET /c/{company_id}/departments)

## Fields

- `id`: integer [REQUIRED for get_candidate, update_candidate, delete_candidate, get_offer] (record ID)
- `company_id`: integer [REQUIRED] (company ID)
- `name`: string [REQUIRED for create_candidate] (candidate full name)
- `email`: string [OPTIONAL] (email address)
- `phone`: string [OPTIONAL] (phone number)
- `photo_url`: string [OPTIONAL] (photo URL)
- `title`: string [REQUIRED for create_offer] (job title)
- `description`: string [OPTIONAL] (job description)
- `department_id`: integer [OPTIONAL] (department ID)
- `pipeline_template_id`: integer [OPTIONAL] (pipeline template ID)

## Example Request Bodies

**Create Candidate:**
```json
{"candidate": {"name": "Jane Doe", "email": "jane@example.com", "phone": "+1234567890"}}
```

**Create Offer:**
```json
{"offer": {"title": "Senior Software Engineer", "description": "Build scalable systems", "department_id": 1}}
```
