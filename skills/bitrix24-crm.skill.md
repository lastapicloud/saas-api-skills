---
name: bitrix24-crm
description: Manage leads, deals, contacts, and tasks via Bitrix24. Use when the user
  mentions bitrix24, bitrix, crm, lead, deal, contact, task.
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
- list_crm_deal_list: List deals (GET /rest/crm.deal.list)
- create_crm_deal_add: Create a deal (POST /rest/crm.deal.add)
- list_crm_contact_list: List contacts (GET /rest/crm.contact.list)
- create_crm_contact_add: Create a contact (POST /rest/crm.contact.add)
- delete_crm.lead.delete: Delete a lead (DELETE /rest/crm.lead.delete)
- create_crm_lead_update: Update a lead (POST /rest/crm.lead.update)
- delete_crm.deal.delete: Delete a deal (DELETE /rest/crm.deal.delete)
- create_crm_deal_update: Update a deal (POST /rest/crm.deal.update)
- delete_crm.contact.delete: Delete a contact (DELETE /rest/crm.contact.delete)
- create_crm_contact_update: Update a contact (POST /rest/crm.contact.update)
- list_tasks_task_list: List tasks (GET /rest/tasks.task.list)
- create_tasks_task_add: Create a task (POST /rest/tasks.task.add)

## Fields

- `TITLE`: string [REQUIRED for create]
- `NAME`: string [OPTIONAL]
- `LAST_NAME`: string [OPTIONAL]

## Example Request Bodies

**Create Lead:**
```json
{"TITLE": "New partnership inquiry", "NAME": "Carlos", "LAST_NAME": "Rivera"}
```

**Create Deal:**
```json
{"TITLE": "Enterprise license renewal", "STAGE_ID": "NEW", "CURRENCY_ID": "USD"}
```
