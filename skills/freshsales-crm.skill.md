---
name: freshsales-crm
description: Manage contacts, accounts, and deals in Freshsales CRM. Use when the
  user mentions freshsales, freshworks crm, freshsales contact, freshsales deal, freshsales
  account.
version: 1.0.0
skill_type: external
base_url_env: FRESHSALES_BASE_URL
auth_env_var: FRESHSALES_API_KEY
auth_type: header
triggers:
  - freshsales
  - freshworks crm
  - freshsales contact
  - freshsales deal
  - freshsales account
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FRESHSALES_BASE_URL and FRESHSALES_API_KEY environment variables.
---

# Freshsales-Crm

Manage contacts, accounts, and deals in Freshsales CRM. Use when the user mentions freshsales, freshworks crm, freshsales contact, freshsales deal, freshsales account.

## API Endpoints

- **GET** `/crm/sales/api/contacts/view/{view_id}` - List contacts by view
- **POST** `/crm/sales/api/contacts` - Create a contact
- **GET** `/crm/sales/api/contacts/{id}` - Get a contact by ID
- **PUT** `/crm/sales/api/contacts/{id}` - Update a contact
- **DELETE** `/crm/sales/api/contacts/{id}` - Delete a contact
- **GET** `/crm/sales/api/deals/view/{view_id}` - List deals by view
- **POST** `/crm/sales/api/deals` - Create a deal
- **GET** `/crm/sales/api/sales_accounts` - List accounts
- **POST** `/crm/sales/api/sales_accounts` - Create an account
- **POST** `/api/contacts`
- **GET** `/api/contacts/` - Use 'include' to embed additional details in the response.
- **GET** `/api/contacts/view/` - You can filter your contacts and also sort them to get a list of specific contacts
- **GET** `/api/contacts/filters`
- **PUT** `/api/contacts/`
- **POST** `/api/contacts/`

## Actions

- get_by_id: List contacts by view (GET /crm/sales/api/contacts/view/{view_id})
- create: Create a contact (POST /crm/sales/api/contacts)
- get_by_id_contacts: Get a contact by ID (GET /crm/sales/api/contacts/{id})
- update: Update a contact (PUT /crm/sales/api/contacts/{id})
- delete: Delete a contact (DELETE /crm/sales/api/contacts/{id})
- get_by_id_view: List deals by view (GET /crm/sales/api/deals/view/{view_id})
- create_deals: Create a deal (POST /crm/sales/api/deals)
- list: List accounts (GET /crm/sales/api/sales_accounts)
- create_sales_accounts: Create an account (POST /crm/sales/api/sales_accounts)
- create_contacts: POST /api/contacts (POST /api/contacts)
- list_contacts: Use 'include' to embed additional details in the response. (GET /api/contacts/)
- list_view: You can filter your contacts and also sort them to get a list of specific contac (GET /api/contacts/view/)
- list_filters: GET /api/contacts/filters (GET /api/contacts/filters)
- put_contacts: PUT /api/contacts/ (PUT /api/contacts/)
- create_contacts_2: POST /api/contacts/ (POST /api/contacts/)

## Fields

- `id`: integer [REQUIRED for get_contact, update_contact, delete_contact] (record ID)
- `view_id`: integer [REQUIRED for list_contacts, list_deals] (view ID)
- `first_name`: string [OPTIONAL] (first name)
- `last_name`: string [REQUIRED for create_contact] (last name)
- `email`: string [OPTIONAL] (email address)
- `mobile_number`: string [OPTIONAL] (mobile phone)
- `job_title`: string [OPTIONAL] (job title)
- `name`: string [REQUIRED for create_deal, create_account] (deal or account name)
- `amount`: number [OPTIONAL] (deal amount)

## Example Request Bodies

**Create Contact:**
```json
{"contact": {"first_name": "Jane", "last_name": "Doe", "email": "jane@example.com", "job_title": "Manager"}}
```

**Create Deal:**
```json
{"deal": {"name": "Enterprise License", "amount": 50000}}
```
