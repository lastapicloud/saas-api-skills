---
name: sendgrid-email
description: Send emails and manage contacts via SendGrid. Use when the user mentions
  sendgrid, email, send email, template, marketing email.
version: 1.0.0
skill_type: external
base_url_env: SENDGRID_BASE_URL
auth_env_var: SENDGRID_API_KEY
auth_type: bearer
triggers:
  - sendgrid
  - email
  - send email
  - template
  - marketing email
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SENDGRID_BASE_URL and SENDGRID_API_KEY environment variables.
---

# Sendgrid-Email

Send emails and manage contacts via SendGrid. Use when the user mentions sendgrid, email, send email, template, marketing email.

## API Endpoints

- **POST** `/mail/send` - Send an email
- **GET** `/marketing/contacts` - List contacts
- **PUT** `/marketing/lists` - Create a contact list
- **GET** `/stats` - Get email stats
- **POST** `/templates` - Create a template
- **POST** `/validations/email` - Validate an email address
- **GET** `/verified_senders` - Get All Verified Senders
- **POST** `/verified_senders` - Create Verified Sender Request
- **PATCH** `/verified_senders/{id}` - Edit Verified Sender
- **DELETE** `/verified_senders/{id}` - Delete Verified Sender
- **GET** `/alerts` - Retrieve all alerts
- **POST** `/alerts` - Create a new Alert
- **PATCH** `/alerts/{alert_id}` - Update an alert
- **DELETE** `/alerts/{alert_id}` - Delete an alert
- **GET** `/api_keys` - Retrieve all API Keys belonging to the authenticated user

## Actions

- create: Send an email (POST /mail/send)
- list: List contacts (GET /marketing/contacts)
- put_lists: Create a contact list (PUT /marketing/lists)
- list_stats: Get email stats (GET /stats)
- create_templates: Create a template (POST /templates)
- create_email: Validate an email address (POST /validations/email)
- list_verified_senders: Get All Verified Senders (GET /verified_senders)
- create_verified_senders: Create Verified Sender Request (POST /verified_senders)
- update: Edit Verified Sender (PATCH /verified_senders/{id})
- delete: Delete Verified Sender (DELETE /verified_senders/{id})
- list_alerts: Retrieve all alerts (GET /alerts)
- create_alerts: Create a new Alert (POST /alerts)
- update_alerts: Update an alert (PATCH /alerts/{alert_id})
- delete_alerts: Delete an alert (DELETE /alerts/{alert_id})
- list_api_keys: Retrieve all API Keys belonging to the authenticated user (GET /api_keys)

## Fields

- `to`: array of objects [REQUIRED for send_email] (recipients, e.g. [{"email": "..."}])
- `from`: object [REQUIRED for send_email] (sender, e.g. {"email": "..."})
- `subject`: string [REQUIRED for send_email] (email subject)
- `content`: array of objects [REQUIRED for send_email] (email body, e.g. [{"type": "text/plain", "value": "..."}])
- `name`: string [REQUIRED for create_contact_list, create_template] (list or template name)
- `email`: string [REQUIRED for validate_email] (email address to validate)
- `start_date`: string [OPTIONAL for get_stats] (stats start date, YYYY-MM-DD)
- `end_date`: string [OPTIONAL for get_stats] (stats end date, YYYY-MM-DD)

## Example Request Bodies

**Send Email:**
```json
{"personalizations": [{"to": [{"email": "user@example.com"}]}], "from": {"email": "sender@example.com"}, "subject": "Hello", "content": [{"type": "text/plain", "value": "Hello from PythonREST!"}]}
```

**Create Template:**
```json
{"name": "Welcome Email", "generation": "dynamic"}
```

**Validate Email:**
```json
{"email": "user@example.com"}
```
