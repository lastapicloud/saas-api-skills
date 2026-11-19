---
name: bitrix24-crm
description: 'Manage leads, deals, contacts, and tasks via Bitrix24. Use when the
  user mentions bitrix24, bitrix, crm, lead, deal, contact, task.

  '
version: 1.0.0
skill_type: external
base_url_env: BITRIX24_BASE_URL
auth_env_var: BITRIX24_ACCESS_TOKEN
auth_type: bearer
triggers:
  - bitrix24
  - bitrix
  - crm
  - lead
  - deal
  - contact
  - task
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BITRIX24_BASE_URL and BITRIX24_ACCESS_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Bitrix24-Crm

Manage leads, deals, contacts, and tasks via Bitrix24. Use when the user mentions bitrix24, bitrix, crm, lead, deal, contact, task.


## API Endpoints

- **GET** `/rest/crm.lead.list` - List leads
- **POST** `/rest/crm.lead.add` - Create a lead
- **GET** `/rest/crm.deal.list` - List deals
- **POST** `/rest/crm.deal.add` - Create a deal
- **GET** `/rest/crm.contact.list` - List contacts
- **POST** `/rest/crm.contact.add` - Create a contact
- **DELETE** `/rest/crm.lead.delete` - Delete a lead
- **POST** `/rest/crm.lead.update` - Update a lead
- **DELETE** `/rest/crm.deal.delete` - Delete a deal
- **POST** `/rest/crm.deal.update` - Update a deal
- **DELETE** `/rest/crm.contact.delete` - Delete a contact
- **POST** `/rest/crm.contact.update` - Update a contact
- **GET** `/rest/tasks.task.list` - List tasks
- **POST** `/rest/tasks.task.add` - Create a task

## Actions

- list: List leads (GET /rest/crm.lead.list)
- create: Create a lead (POST /rest/crm.lead.add)
- list_deals: List deals (GET /rest/crm.deal.list)
- create_deal: Create a deal (POST /rest/crm.deal.add)
- list_contacts: List contacts (GET /rest/crm.contact.list)
- create_contact: Create a contact (POST /rest/crm.contact.add)
- delete_crm.lead.delete: Delete a lead (DELETE /rest/crm.lead.delete)
- update_lead: Update a lead (POST /rest/crm.lead.update)
- delete_crm.deal.delete: Delete a deal (DELETE /rest/crm.deal.delete)
- update_deal: Update a deal (POST /rest/crm.deal.update)
- delete_crm.contact.delete: Delete a contact (DELETE /rest/crm.contact.delete)
- update_contact: Update a contact (POST /rest/crm.contact.update)
- list_tasks: List tasks (GET /rest/tasks.task.list)
- create_task: Create a task (POST /rest/tasks.task.add)

## Fields

- `TITLE`: string [REQUIRED for create] — Title or heading
- `NAME`: string [OPTIONAL] — Display name
- `LAST_NAME`: string [OPTIONAL] — Last display name

## Example Request Bodies

**Create Lead:**
```json
{"TITLE": "New partnership inquiry", "NAME": "Carlos", "LAST_NAME": "Rivera"}
```

**Create Deal:**
```json
{"TITLE": "Enterprise license renewal", "STAGE_ID": "NEW", "CURRENCY_ID": "USD"}
```

## Response

**Crm.Lead.List object:**
- `id`: string — Unique crm.lead.list identifier
- `name`: string — Crm.Lead.List name or title
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
