---
name: mautic-marketing
description: 'Manage contacts, campaigns, and emails via Mautic. Use when the user
  mentions mautic, marketing, contact, campaign, email, automation.

  '
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
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
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
- delete: Delete contact (DELETE /api/contacts/{id}/delete)
- list_campaigns: List campaigns (GET /api/campaigns)
- list_emails: List emails (GET /api/emails)
- send_email: Send email (POST /api/emails/{id}/send)

## Fields

- `email`: string [OPTIONAL] — Email address
- `firstname`: string [OPTIONAL] — First display name
- `lastname`: string [OPTIONAL] — Last display name

## Example Request Bodies

**Create Contact:**
```json
{"email": "lead@example.com", "firstname": "Maria", "lastname": "Garcia"}
```

**Send Email:**
```json
{"tokens": {"greeting": "Hello Maria"}}
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
