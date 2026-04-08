---
name: mailersend-email
description: Send emails and manage templates via MailerSend. Use when the user mentions
  mailersend, email, transactional email, template, domain.
version: 1.0.0
skill_type: external
base_url_env: MAILERSEND_BASE_URL
auth_env_var: MAILERSEND_API_TOKEN
auth_type: bearer
triggers:
  - mailersend
  - email
  - transactional email
  - template
  - domain
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MAILERSEND_BASE_URL and MAILERSEND_API_TOKEN environment variables.
---

# Mailersend-Email

Send emails and manage templates via MailerSend. Use when the user mentions mailersend, email, transactional email, template, domain.

## API Endpoints

- **POST** `/v1/email` - Send email
- **GET** `/v1/activity` - List activity
- **GET** `/v1/templates` - List templates
- **GET** `/v1/templates/{template_id}` - Get template
- **GET** `/v1/domains` - List domains
- **POST** `/v1/domains` - Add domain
- **GET** `/v1/recipients` - List recipients
- **POST** `/v1/email/bulk` - Send bulk email

## Actions

- create: Send email (POST /v1/email)
- list: List activity (GET /v1/activity)
- list_templates: List templates (GET /v1/templates)
- get_by_id: Get template (GET /v1/templates/{template_id})
- list_domains: List domains (GET /v1/domains)
- create_domains: Add domain (POST /v1/domains)
- list_recipients: List recipients (GET /v1/recipients)
- create_bulk: Send bulk email (POST /v1/email/bulk)

## Fields

- `from`: object [REQUIRED for send] (email, name)
- `to`: array [REQUIRED for send]
- `subject`: string [REQUIRED for send]
- `html`: string [OPTIONAL]
- `text`: string [OPTIONAL]

## Example Request Bodies

**Send Email:**
```json
{"from": {"email": "noreply@example.com", "name": "Example App"}, "to": [{"email": "recipient@example.com", "name": "Jane Doe"}], "subject": "Welcome to Example App", "html": "<h1>Welcome!</h1><p>Thanks for signing up.</p>"}
```

**Add Domain:**
```json
{"name": "mail.example.com"}
```
