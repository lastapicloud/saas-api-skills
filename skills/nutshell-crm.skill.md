---
name: nutshell-crm
description: Manage contacts, leads, and accounts in Nutshell CRM. Use when the user
  mentions nutshell, nutshell crm, nutshell lead, nutshell contact, nutshell account.
version: 1.0.0
skill_type: external
base_url_env: NUTSHELL_BASE_URL
auth_env_var: NUTSHELL_API_KEY
auth_type: basic
triggers:
  - nutshell
  - nutshell crm
  - nutshell lead
  - nutshell contact
  - nutshell account
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires NUTSHELL_BASE_URL and NUTSHELL_API_KEY environment variables.
---

# Nutshell-Crm

Manage contacts, leads, and accounts in Nutshell CRM. Use when the user mentions nutshell, nutshell crm, nutshell lead, nutshell contact, nutshell account.

## API Endpoints

- **GET** `/api/v1/contacts` - List contacts
- **POST** `/api/v1/contacts` - Create a contact
- **GET** `/api/v1/contacts/{id}` - Get a contact by ID
- **PUT** `/api/v1/contacts/{id}` - Update a contact
- **DELETE** `/api/v1/contacts/{id}` - Delete a contact
- **GET** `/api/v1/leads` - List leads
- **POST** `/api/v1/leads` - Create a lead
- **GET** `/api/v1/leads/{id}` - Get a lead by ID
- **GET** `/api/v1/accounts` - List accounts
- **POST** `/api/v1/accounts` - Create an account

## Actions

- list: List contacts (GET /api/v1/contacts)
- create: Create a contact (POST /api/v1/contacts)
- get_by_id: Get a contact by ID (GET /api/v1/contacts/{id})
- update: Update a contact (PUT /api/v1/contacts/{id})
- delete: Delete a contact (DELETE /api/v1/contacts/{id})
- list_leads: List leads (GET /api/v1/leads)
- create_leads: Create a lead (POST /api/v1/leads)
- get_by_id_leads: Get a lead by ID (GET /api/v1/leads/{id})
- list_accounts: List accounts (GET /api/v1/accounts)
- create_accounts: Create an account (POST /api/v1/accounts)

## Fields

- `id`: integer [REQUIRED for get_contact, update_contact, delete_contact, get_lead] (record ID)
- `name`: string [REQUIRED for create_contact, create_account] (name)
- `email`: string [OPTIONAL] (email address)
- `phone`: string [OPTIONAL] (phone number)
- `description`: string [OPTIONAL] (lead or account description)
- `value`: number [OPTIONAL] (lead value)
- `confidence`: integer [OPTIONAL] (lead confidence percentage)

## Example Request Bodies

**Create Contact:**
```json
{"name": "Jane Doe", "email": "jane@example.com", "phone": "+1234567890"}
```

**Create Lead:**
```json
{"name": "Enterprise Deal", "value": 50000, "confidence": 75}
```
