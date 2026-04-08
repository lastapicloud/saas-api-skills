---
name: close-crm
description: Manage leads, contacts, opportunities, and activities in Close CRM. Use
  when the user mentions close, close crm, close lead, close opportunity, close activity.
version: 1.0.0
skill_type: external
base_url_env: CLOSE_BASE_URL
auth_env_var: CLOSE_API_KEY
auth_type: basic
triggers:
  - close
  - close crm
  - close lead
  - close opportunity
  - close activity
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CLOSE_BASE_URL and CLOSE_API_KEY environment variables.
---

# Close-Crm

Manage leads, contacts, opportunities, and activities in Close CRM. Use when the user mentions close, close crm, close lead, close opportunity, close activity.

## API Endpoints

- **GET** `/api/v1/lead/` - List leads
- **POST** `/api/v1/lead/` - Create a lead
- **GET** `/api/v1/lead/{id}/` - Get a lead by ID
- **PUT** `/api/v1/lead/{id}/` - Update a lead
- **DELETE** `/api/v1/lead/{id}/` - Delete a lead
- **GET** `/api/v1/contact/` - List contacts
- **POST** `/api/v1/contact/` - Create a contact
- **GET** `/api/v1/opportunity/` - List opportunities
- **POST** `/api/v1/opportunity/` - Create an opportunity
- **GET** `/api/v1/activity/` - List activities
- **GET** `/lead/{`
- **POST** `/lead/` - Contacts, addresses, and custom fields can all be nested in the lead. Currently, activities, tasks, and opportunities must be posted separately.
- **GET** `/lead/{id}/{`
- **PUT** `/lead/{id}/` - Supports non-destructive patches.
- **DELETE** `/lead/{id}/`

## Actions

- list: List leads (GET /api/v1/lead/)
- create: Create a lead (POST /api/v1/lead/)
- get_by_id: Get a lead by ID (GET /api/v1/lead/{id}/)
- update: Update a lead (PUT /api/v1/lead/{id}/)
- delete: Delete a lead (DELETE /api/v1/lead/{id}/)
- list_contact: List contacts (GET /api/v1/contact/)
- create_contact: Create a contact (POST /api/v1/contact/)
- list_opportunity: List opportunities (GET /api/v1/opportunity/)
- create_opportunity: Create an opportunity (POST /api/v1/opportunity/)
- list_activity: List activities (GET /api/v1/activity/)
- list_lead: GET /lead/{ (GET /lead/{)
- create_lead: Contacts, addresses, and custom fields can all be nested in the lead. Currently, (POST /lead/)
- list_lead_2: GET /lead/{id}/{ (GET /lead/{id}/{)
- update_lead: Supports non-destructive patches. (PUT /lead/{id}/)
- delete_lead: DELETE /lead/{id}/ (DELETE /lead/{id}/)

## Fields

- `id`: string [REQUIRED for get_lead, update_lead, delete_lead] (record ID)
- `name`: string [REQUIRED for create_lead] (lead name)
- `contacts`: array [OPTIONAL] (embedded contact objects)
- `status_id`: string [OPTIONAL] (lead status ID)
- `lead_id`: string [REQUIRED for create_contact, create_opportunity] (associated lead ID)
- `value`: number [OPTIONAL] (opportunity value in cents)
- `value_period`: string [OPTIONAL] (one_time, monthly, annual)
- `confidence`: integer [OPTIONAL] (opportunity confidence 0-100)
- `note`: string [OPTIONAL] (note text)

## Example Request Bodies

**Create Lead:**
```json
{"name": "Acme Corp", "contacts": [{"name": "Jane Doe", "emails": [{"type": "office", "email": "jane@acme.com"}]}]}
```

**Create Opportunity:**
```json
{"lead_id": "lead_abc123", "value": 5000000, "value_period": "one_time", "confidence": 75}
```
