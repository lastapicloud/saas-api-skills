---
name: attio-crm
description: Manage contacts, companies, and deals via Attio CRM. Use when the user
  mentions attio, crm, contact, company, deal, pipeline, lead.
version: 1.0.0
skill_type: external
base_url_env: ATTIO_BASE_URL
auth_env_var: ATTIO_API_KEY
auth_type: bearer
triggers:
  - attio
  - crm
  - contact
  - company
  - deal
  - pipeline
  - lead
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ATTIO_BASE_URL and ATTIO_API_KEY environment variables.
---

# Attio-Crm

Manage contacts, companies, and deals via Attio CRM. Use when the user mentions attio, crm, contact, company, deal, pipeline, lead.

## API Endpoints

- **GET** `/v2/objects/people/records/query` - List people
- **POST** `/v2/objects/people/records` - Create a person
- **GET** `/v2/objects/people/records/{record_id}` - Get person by ID
- **PATCH** `/v2/objects/people/records/{record_id}` - Update a person
- **DELETE** `/v2/objects/people/records/{record_id}` - Delete a person
- **POST** `/v2/objects/companies/records/query` - List companies
- **POST** `/v2/objects/companies/records` - Create a company
- **GET** `/v2/lists` - List all lists
- **GET** `/v2/tasks` - List tasks
- **POST** `/v2/tasks` - Create a task
- **PATCH** `/v2/tasks/{task_id}` - Update a task
- **DELETE** `/v2/tasks/{task_id}` - Delete a task
- **GET** `/scim/v2/Schemas` - List SCIM schemas
- **POST** `/scim/v2/Users` - Create SCIM user
- **PUT** `/scim/v2/Users/{user_id}` - Update SCIM user

## Actions

- query: List people (GET /v2/objects/people/records/query)
- create: Create a person (POST /v2/objects/people/records)
- get_by_id: Get person by ID (GET /v2/objects/people/records/{record_id})
- update: Update a person (PATCH /v2/objects/people/records/{record_id})
- delete: Delete a person (DELETE /v2/objects/people/records/{record_id})
- query_records: List companies (POST /v2/objects/companies/records/query)
- create_records: Create a company (POST /v2/objects/companies/records)
- list: List all lists (GET /v2/lists)
- list_tasks: List tasks (GET /v2/tasks)
- create_tasks: Create a task (POST /v2/tasks)
- update_tasks: Update a task (PATCH /v2/tasks/{task_id})
- delete_tasks: Delete a task (DELETE /v2/tasks/{task_id})
- list_schemas: List SCIM schemas (GET /scim/v2/Schemas)
- create_users: Create SCIM user (POST /scim/v2/Users)
- update_users: Update SCIM user (PUT /scim/v2/Users/{user_id})

## Fields

- `values`: object [REQUIRED for create] (attribute values)
- `record_id`: string [REQUIRED for get/update/delete]

## Example Request Bodies

**Create Person:**
```json
{"values": {"name": [{"first_name": "Jane", "last_name": "Doe"}], "email_addresses": [{"email_address": "jane@example.com"}]}}
```

**Update Person:**
```json
{"values": {"email_addresses": [{"email_address": "jane.doe@newdomain.com"}]}}
