---
name: mautic-marketing
description: Manage contacts, campaigns, and emails via Mautic. Use when the user
  mentions mautic, marketing, contact, campaign, email, automation.
version: 1.0.0
skill_type: external
base_url_env: MAUTIC_BASE_URL
auth_env_var: MAUTIC_ACCESS_TOKEN
auth_type: bearer
triggers:
  - mautic
  - marketing
  - contact
  - campaign
  - email
  - automation
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MAUTIC_BASE_URL and MAUTIC_ACCESS_TOKEN environment variables.
---

# Mautic-Marketing

Manage contacts, campaigns, and emails via Mautic. Use when the user mentions mautic, marketing, contact, campaign, email, automation.

## API Endpoints

- **GET** `/api/contacts` - List contacts
- **POST** `/api/contacts/new` - Create contact
- **GET** `/api/contacts/{id}` - Get contact
- **PATCH** `/api/contacts/{id}/edit` - Update contact
- **DELETE** `/api/contacts/{id}/delete` - Delete contact
- **GET** `/api/campaigns` - List campaigns
- **GET** `/api/emails` - List emails
- **POST** `/api/emails/{id}/send` - Send email

## Actions

- list: List contacts (GET /api/contacts)
- create: Create contact (POST /api/contacts/new)
- get_by_id: Get contact (GET /api/contacts/{id})
- patch_edit: Update contact (PATCH /api/contacts/{id}/edit)
- delete_delete: Delete contact (DELETE /api/contacts/{id}/delete)
- list_campaigns: List campaigns (GET /api/campaigns)
- list_emails: List emails (GET /api/emails)
- create_send: Send email (POST /api/emails/{id}/send)

## Fields

- `email`: string [OPTIONAL]
- `firstname`: string [OPTIONAL]
- `lastname`: string [OPTIONAL]

## Example Request Bodies

**Create Contact:**
```json
{"email": "lead@example.com", "firstname": "Maria", "lastname": "Garcia"}
```

**Send Email:**
```json
{"tokens": {"greeting": "Hello Maria"}}
```
