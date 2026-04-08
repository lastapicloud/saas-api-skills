---
name: brevo-email
description: Send emails and manage contacts via Brevo. Use when the user mentions
  brevo, sendinblue, email, send email, contact, campaign.
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
- create_contacts: Create a contact (POST /v3/contacts)
- get_by_id: Get a contact (GET /v3/contacts/{identifier})
- update: Update a contact (PUT /v3/contacts/{identifier})
- delete: Delete a contact (DELETE /v3/contacts/{identifier})
- list_emailcampaigns: List campaigns (GET /v3/emailCampaigns)
- create_emailcampaigns: Create a campaign (POST /v3/emailCampaigns)
- list_events: Get email events (GET /v3/smtp/statistics/events)
- list_lists: List contact lists (GET /v3/contacts/lists)

## Fields

- `sender`: object [REQUIRED for send] with `email`, `name`
- `to`: array [REQUIRED for send] with `email`, `name`
- `subject`: string [REQUIRED for send]
- `htmlContent`: string [OPTIONAL]
- `textContent`: string [OPTIONAL]
- `email`: string [REQUIRED for create contact]
- `attributes`: object [OPTIONAL for contact]

## Example Request Bodies

**Send Email:**
```json
{"sender": {"email": "noreply@example.com", "name": "My App"}, "to": [{"email": "user@example.com", "name": "User"}], "subject": "Welcome!", "htmlContent": "<p>Hello!</p>"}
```

**Create Contact:**
```json
{"email": "contact@example.com", "attributes": {"FIRSTNAME": "Jane", "LASTNAME": "Doe"}}
