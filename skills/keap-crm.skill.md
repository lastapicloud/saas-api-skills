---
name: keap-crm
description: 'Manage contacts, opportunities, and tasks in Keap (Infusionsoft) CRM.
  Use when the user mentions keap, infusionsoft, keap contact, keap opportunity, keap
  task.

  '
version: 1.0.0
skill_type: external
base_url_env: KEAP_BASE_URL
auth_env_var: KEAP_API_TOKEN
auth_type: bearer
triggers:
  - keap
  - infusionsoft
  - keap contact
  - keap opportunity
  - keap task
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires KEAP_BASE_URL and KEAP_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Keap-Crm

Manage contacts, opportunities, and tasks in Keap (Infusionsoft) CRM. Use when the user mentions keap, infusionsoft, keap contact, keap opportunity, keap task.


## API Endpoints

- **GET** `/crm/rest/v2/contacts` - List contacts
- **POST** `/crm/rest/v2/contacts` - Create a contact
- **GET** `/crm/rest/v2/contacts/{contact_id}` - Get a contact by ID
- **PATCH** `/crm/rest/v2/contacts/{contact_id}` - Update a contact
- **DELETE** `/crm/rest/v2/contacts/{contact_id}` - Delete a contact
- **GET** `/crm/rest/v2/opportunities` - List opportunities
- **POST** `/crm/rest/v2/opportunities` - Create an opportunity
- **GET** `/crm/rest/v2/tasks` - List tasks
- **POST** `/crm/rest/v2/tasks` - Create a task

## Actions

- list: List contacts (GET /crm/rest/v2/contacts)
- create: Create a contact (POST /crm/rest/v2/contacts)
- get_by_id: Get a contact by ID (GET /crm/rest/v2/contacts/{contact_id})
- update: Update a contact (PATCH /crm/rest/v2/contacts/{contact_id})
- delete: Delete a contact (DELETE /crm/rest/v2/contacts/{contact_id})
- list_opportunities: List opportunities (GET /crm/rest/v2/opportunities)
- create_opportunity: Create an opportunity (POST /crm/rest/v2/opportunities)
- list_tasks: List tasks (GET /crm/rest/v2/tasks)
- create_task: Create a task (POST /crm/rest/v2/tasks)

## Fields

- `contact_id`: integer [REQUIRED for get_contact, update_contact, delete_contact] (contact ID) — Contact unique identifier
- `given_name`: string [OPTIONAL] (first name) — Given display name
- `family_name`: string [OPTIONAL] (last name) — Family display name
- `email_addresses`: array [OPTIONAL] (email addresses with email and field fields) — List of email addresses
- `phone_numbers`: array [OPTIONAL] (phone numbers with number and field fields) — List of phone numbers
- `opportunity_title`: string [REQUIRED for create_opportunity] (opportunity title) — Opportunity title or heading
- `contact`: object [REQUIRED for create_opportunity] (contact reference with id field) — Contact configuration
- `stage`: object [OPTIONAL] (pipeline stage reference) — Stage configuration
- `title`: string [REQUIRED for create_task] (task title) — Title or heading
- `due_date`: string [OPTIONAL] (task due date in ISO 8601 format) — Due Date

## Example Request Bodies

**Create Contact:**
```json
{"given_name": "Jane", "family_name": "Doe", "email_addresses": [{"email": "jane@example.com", "field": "EMAIL1"}]}
```

**Create Opportunity:**
```json
{"opportunity_title": "Enterprise License", "contact": {"id": 123}, "estimated_close_date": "2026-06-01"}
```

## Response

**Contact object:**
- `id`: string — Unique contact identifier
- `name`: string — Contact name or title
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
