---
name: folk-crm
description: Manage contacts and pipelines via Folk CRM. Use when the user mentions
  folk, crm, contact, company, pipeline, deal.
version: 1.0.0
skill_type: external
base_url_env: FOLK_BASE_URL
auth_env_var: FOLK_API_KEY
auth_type: bearer
triggers:
  - folk
  - crm
  - contact
  - company
  - pipeline
  - deal
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FOLK_BASE_URL and FOLK_API_KEY environment variables.
---

# Folk-Crm

Manage contacts and pipelines via Folk CRM. Use when the user mentions folk, crm, contact, company, pipeline, deal.

## API Endpoints

- **GET** `/v1/persons` - List persons
- **POST** `/v1/persons` - Create person
- **GET** `/v1/persons/{id}` - Get person
- **PATCH** `/v1/persons/{id}` - Update person
- **DELETE** `/v1/persons/{id}` - Delete person
- **GET** `/v1/companies` - List companies
- **POST** `/v1/companies` - Create company
- **GET** `/v1/groups` - List groups

## Actions

- list: List persons (GET /v1/persons)
- create: Create person (POST /v1/persons)
- get_by_id: Get person (GET /v1/persons/{id})
- update: Update person (PATCH /v1/persons/{id})
- delete: Delete person (DELETE /v1/persons/{id})
- list_companies: List companies (GET /v1/companies)
- create_companies: Create company (POST /v1/companies)
- list_groups: List groups (GET /v1/groups)

## Fields

- `firstName`: string [OPTIONAL]
- `lastName`: string [OPTIONAL]
- `emails`: array [OPTIONAL]

## Example Request Bodies

**Create Person:**
```json
{"firstName": "Alex", "lastName": "Johnson", "emails": ["alex@example.com"]}
```

**Update Person:**
```json
{"firstName": "Alexander", "emails": ["alex.johnson@example.com"]}
