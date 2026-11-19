---
name: brevo-email
description: 'Send emails and manage contacts via Brevo. Use when the user mentions
  brevo, sendinblue, email, send email, contact, campaign.

  '
version: 1.0.0
skill_type: external
base_url_env: BREVO_BASE_URL
auth_env_var: BREVO_API_KEY
auth_type: header
triggers:
  - brevo
  - sendinblue
  - email
  - send email
  - contact
  - campaign
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BREVO_BASE_URL and BREVO_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Brevo-Email

Send emails and manage contacts via Brevo. Use when the user mentions brevo, sendinblue, email, send email, contact, campaign.


## API Endpoints

- **POST** `/v3/smtp/email` - Send a transactional email
- **GET** `/v3/contacts` - List contacts
- **POST** `/v3/contacts` - Create a contact
- **GET** `/v3/contacts/{identifier}` - Get a contact
- **PUT** `/v3/contacts/{identifier}` - Update a contact
- **DELETE** `/v3/contacts/{identifier}` - Delete a contact
- **GET** `/v3/emailCampaigns` - List campaigns
- **POST** `/v3/emailCampaigns` - Create a campaign
- **GET** `/v3/smtp/statistics/events` - Get email events
- **GET** `/v3/contacts/lists` - List contact lists

## Actions

- create: Send a transactional email (POST /v3/smtp/email)
- list: List contacts (GET /v3/contacts)
- create_contact: Create a contact (POST /v3/contacts)
- get_by_id: Get a contact (GET /v3/contacts/{identifier})
- update: Update a contact (PUT /v3/contacts/{identifier})
- delete: Delete a contact (DELETE /v3/contacts/{identifier})
- list_campaigns: List campaigns (GET /v3/emailCampaigns)
- create_campaign: Create a campaign (POST /v3/emailCampaigns)
- get_email_events: Get email events (GET /v3/smtp/statistics/events)
- list_contact_lists: List contact lists (GET /v3/contacts/lists)

## Fields

- `sender`: object [REQUIRED for send] with `email`, `name` — Sender configuration
- `to`: array [REQUIRED for send] with `email`, `name` — List of to
- `subject`: string [REQUIRED for send] — Subject
- `htmlContent`: string [OPTIONAL] — Html content body
- `textContent`: string [OPTIONAL] — Text content body
- `email`: string [REQUIRED for create contact] — Email address
- `attributes`: object [OPTIONAL for contact] — Attributes configuration

## Example Request Bodies

**Send Email:**
```json
{"sender": {"email": "noreply@example.com", "name": "My App"}, "to": [{"email": "user@example.com", "name": "User"}], "subject": "Welcome!", "htmlContent": "Hello!"}
```

**Create Contact:**
```json
{"email": "contact@example.com", "attributes": {"FIRSTNAME": "Jane", "LASTNAME": "Doe"}}

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
