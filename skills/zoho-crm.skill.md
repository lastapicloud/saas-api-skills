---
name: zoho-crm
description: Manage leads, contacts, deals, and accounts in Zoho CRM. Use when the
  user mentions zoho, zoho crm, zoho lead, zoho contact, zoho deal, zoho account.
version: 1.0.0
skill_type: external
base_url_env: ZOHO_CRM_BASE_URL
auth_env_var: ZOHO_CRM_ACCESS_TOKEN
auth_type: bearer
triggers:
  - zoho
  - zoho crm
  - zoho lead
  - zoho contact
  - zoho deal
  - zoho account
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ZOHO_CRM_BASE_URL and ZOHO_CRM_ACCESS_TOKEN environment variables.
---

# Zoho-Crm

Manage leads, contacts, deals, and accounts in Zoho CRM. Use when the user mentions zoho, zoho crm, zoho lead, zoho contact, zoho deal, zoho account.

## API Endpoints

- **GET** `/crm/v8/Leads` - List leads
- **POST** `/crm/v8/Leads` - Create a lead
- **GET** `/crm/v8/Leads/{record_id}` - Get a lead by ID
- **PUT** `/crm/v8/Leads/{record_id}` - Update a lead
- **DELETE** `/crm/v8/Leads/{record_id}` - Delete a lead
- **GET** `/crm/v8/Contacts` - List contacts
- **POST** `/crm/v8/Contacts` - Create a contact
- **GET** `/crm/v8/Deals` - List deals
- **POST** `/crm/v8/Deals` - Create a deal
- **GET** `/crm/v8/Accounts` - List accounts
- **GET** `/{module_api_name}` - GET /{module_api_name}/{record_id}
- **GET** `/{module_api_name}GET`
- **GET** `/{module_api_name}/{record_id}`

## Actions

- list: List leads (GET /crm/v8/Leads)
- create: Create a lead (POST /crm/v8/Leads)
- get_by_id: Get a lead by ID (GET /crm/v8/Leads/{record_id})
- update: Update a lead (PUT /crm/v8/Leads/{record_id})
- delete: Delete a lead (DELETE /crm/v8/Leads/{record_id})
- list_contacts: List contacts (GET /crm/v8/Contacts)
- create_contacts: Create a contact (POST /crm/v8/Contacts)
- list_deals: List deals (GET /crm/v8/Deals)
- create_deals: Create a deal (POST /crm/v8/Deals)
- list_accounts: List accounts (GET /crm/v8/Accounts)
- get_by_id_resource: GET /{module_api_name}/{record_id} (GET /{module_api_name})
- list_resource: GET /{module_api_name}GET (GET /{module_api_name}GET)
- get_by_id_resource_2: GET /{module_api_name}/{record_id} (GET /{module_api_name}/{record_id})

## Fields

- `record_id`: string [REQUIRED for get_lead, update_lead, delete_lead] (record ID)
- `Last_Name`: string [REQUIRED for create_lead, create_contact] (last name)
- `First_Name`: string [OPTIONAL] (first name)
- `Email`: string [OPTIONAL] (email address)
- `Company`: string [REQUIRED for create_lead] (company name)
- `Phone`: string [OPTIONAL] (phone number)
- `Deal_Name`: string [REQUIRED for create_deal] (deal name)
- `Stage`: string [REQUIRED for create_deal] (deal stage)
- `Amount`: number [OPTIONAL] (deal amount)
- `Account_Name`: string [OPTIONAL] (account name)

## Example Request Bodies

**Create Lead:**
```json
{"data": [{"Last_Name": "Doe", "First_Name": "Jane", "Email": "jane@example.com", "Company": "Acme Corp"}]}
```

**Create Deal:**
```json
{"data": [{"Deal_Name": "Enterprise License", "Stage": "Qualification", "Amount": 50000}]}
```
