---
name: pipedrive-crm
description: Manage deals, contacts, organizations, and pipelines in Pipedrive. Use
  when the user mentions pipedrive, deal, contact, person, organization, pipeline,
  CRM, lead.
version: 1.0.0
skill_type: external
base_url_env: PIPEDRIVE_BASE_URL
auth_env_var: PIPEDRIVE_API_TOKEN
auth_type: header
triggers:
  - pipedrive
  - deal
  - contact
  - person
  - organization
  - pipeline
  - CRM
  - lead
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PIPEDRIVE_BASE_URL and PIPEDRIVE_API_TOKEN environment variables.
---

# Pipedrive-Crm

Manage deals, contacts, organizations, and pipelines in Pipedrive. Use when the user mentions pipedrive, deal, contact, person, organization, pipeline, CRM, lead.

## API Endpoints

- **GET** `/deals` - List deals
- **POST** `/deals` - Create a deal
- **GET** `/deals/{id}` - Get a deal
- **PUT** `/deals/{id}` - Update a deal
- **GET** `/persons` - List persons (contacts)
- **POST** `/persons` - Create a person
- **GET** `/organizations` - List organizations
- **POST** `/organizations` - Create an organization
- **GET** `/leads/search` - Search leads
- **POST** `/leads` - Add a lead
- **PATCH** `/leads/{id}` - Update a lead
- **DELETE** `/leads/{id}` - Delete a lead
- **GET** `/files` - Get all files
- **POST** `/files` - Add file
- **PUT** `/files/{id}` - Update file details

## Actions

- list: List deals (GET /deals)
- create: Create a deal (POST /deals)
- get_by_id: Get a deal (GET /deals/{id})
- update: Update a deal (PUT /deals/{id})
- list_persons: List persons (contacts) (GET /persons)
- create_persons: Create a person (POST /persons)
- list_organizations: List organizations (GET /organizations)
- create_organizations: Create an organization (POST /organizations)
- search: Search leads (GET /leads/search)
- create_leads: Add a lead (POST /leads)
- update_leads: Update a lead (PATCH /leads/{id})
- delete: Delete a lead (DELETE /leads/{id})
- list_files: Get all files (GET /files)
- create_files: Add file (POST /files)
- update_files: Update file details (PUT /files/{id})

## Fields

- `id`: integer [REQUIRED for get/update actions] (resource ID)
- `title`: string [REQUIRED for create_deal] (deal title)
- `value`: number [OPTIONAL for create_deal] (deal value)
- `currency`: string [OPTIONAL for create_deal] (three-letter currency code)
- `person_id`: integer [OPTIONAL for create_deal] (associated person ID)
- `org_id`: integer [OPTIONAL for create_deal] (associated organization ID)
- `pipeline_id`: integer [OPTIONAL for create_deal] (pipeline ID)
- `stage_id`: integer [OPTIONAL for create_deal] (pipeline stage ID)
- `name`: string [REQUIRED for create_person, create_organization] (person or org name)
- `email`: string [OPTIONAL for create_person] (person email)
- `phone`: string [OPTIONAL for create_person] (person phone)
- `status`: string [OPTIONAL] (filter: open, won, lost, deleted)
- `limit`: integer [OPTIONAL] (results per page)
- `start`: integer [OPTIONAL] (pagination offset)

## Example Request Bodies

**Create Deal:**
```json
{"title": "Enterprise Plan Upgrade", "value": 5000, "currency": "USD", "person_id": 123, "pipeline_id": 1}
```

**Create Person:**
```json
{"name": "Jane Doe", "email": [{"value": "jane@example.com", "primary": true}], "phone": [{"value": "+1234567890", "primary": true}]}
```

**Create Organization:**
```json
{"name": "Acme Corp"}
```
