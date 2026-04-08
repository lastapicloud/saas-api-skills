---
name: activecampaign-crm
description: Manage contacts, deals, and automations in ActiveCampaign. Use when the
  user mentions activecampaign, active campaign, activecampaign contact, activecampaign
  deal, activecampaign automation.
version: 1.0.0
skill_type: external
base_url_env: ACTIVECAMPAIGN_BASE_URL
auth_env_var: ACTIVECAMPAIGN_API_KEY
auth_type: header
triggers:
  - activecampaign
  - active campaign
  - activecampaign contact
  - activecampaign deal
  - activecampaign automation
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ACTIVECAMPAIGN_BASE_URL and ACTIVECAMPAIGN_API_KEY environment
  variables.
---

# Activecampaign-Crm

Manage contacts, deals, and automations in ActiveCampaign. Use when the user mentions activecampaign, active campaign, activecampaign contact, activecampaign deal, activecampaign automation.

## API Endpoints

- **GET** `/api/3/contacts` - List contacts
- **POST** `/api/3/contacts` - Create a contact
- **GET** `/api/3/contacts/{id}` - Get a contact by ID
- **PUT** `/api/3/contacts/{id}` - Update a contact
- **DELETE** `/api/3/contacts/{id}` - Delete a contact
- **GET** `/api/3/deals` - List deals
- **POST** `/api/3/deals` - Create a deal
- **GET** `/api/3/dealStages` - List deal stages
- **GET** `/api/3/dealPipelines` - List deal pipelines
- **GET** `/api/3/automations` - List automations
- **POST** `/email`
- **POST** `/email/batch`

## Actions

- list: List contacts (GET /api/3/contacts)
- create: Create a contact (POST /api/3/contacts)
- get_by_id: Get a contact by ID (GET /api/3/contacts/{id})
- update: Update a contact (PUT /api/3/contacts/{id})
- delete: Delete a contact (DELETE /api/3/contacts/{id})
- list_deals: List deals (GET /api/3/deals)
- create_deals: Create a deal (POST /api/3/deals)
- list_dealstages: List deal stages (GET /api/3/dealStages)
- list_dealpipelines: List deal pipelines (GET /api/3/dealPipelines)
- list_automations: List automations (GET /api/3/automations)
- create_email: POST /email (POST /email)
- create_batch: POST /email/batch (POST /email/batch)

## Fields

- `id`: integer [REQUIRED for get_contact, update_contact, delete_contact] (record ID)
- `email`: string [REQUIRED for create_contact] (contact email)
- `firstName`: string [OPTIONAL] (first name)
- `lastName`: string [OPTIONAL] (last name)
- `phone`: string [OPTIONAL] (phone number)
- `title`: string [REQUIRED for create_deal] (deal title)
- `value`: integer [OPTIONAL] (deal value in cents)
- `currency`: string [OPTIONAL] (deal currency code, e.g. usd)
- `group`: string [OPTIONAL] (pipeline ID)
- `stage`: string [OPTIONAL] (stage ID)

## Example Request Bodies

**Create Contact:**
```json
{"contact": {"email": "jane@example.com", "firstName": "Jane", "lastName": "Doe", "phone": "+1234567890"}}
```

**Create Deal:**
```json
{"deal": {"title": "Enterprise License", "value": 5000000, "currency": "usd", "group": "1", "stage": "1"}}
```
