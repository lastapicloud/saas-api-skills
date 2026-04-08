---
name: postmark-email
description: Send emails, manage templates, and track delivery via the Postmark API.
  Use when the user mentions postmark, email, send email, bounce, delivery.
version: 1.0.0
skill_type: external
base_url_env: POSTMARK_BASE_URL
auth_env_var: POSTMARK_SERVER_TOKEN
auth_type: header
triggers:
  - postmark
  - email
  - send email
  - bounce
  - delivery
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires POSTMARK_BASE_URL and POSTMARK_SERVER_TOKEN environment variables.
---

# Postmark-Email

Send emails, manage templates, and track delivery via the Postmark API. Use when the user mentions postmark, email, send email, bounce, delivery.

## API Endpoints

- **POST** `/email` - Send a single email
- **POST** `/email/batch` - Send a batch of emails
- **POST** `/email/withTemplate` - Send an email using a template
- **GET** `/templates` - List templates
- **GET** `/bounces` - Get bounces
- **GET** `/deliverystats` - Get delivery statistics
- **POST** `/templates` - Create a Template
- **PUT** `/templates/{templateIdOrAlias}` - Update a Template
- **DELETE** `/templates/{templateIdOrAlias}` - Delete a Template
- **GET** `/triggers/inboundrules` - List inbound rule triggers
- **POST** `/triggers/inboundrules` - Create an inbound rule trigger
- **DELETE** `/triggers/inboundrules/{triggerid}` - Delete a single trigger
- **GET** `/bounces/{bounceid}` - Get a single bounce
- **PUT** `/bounces/{bounceid}/activate` - Activate a bounce
- **GET** `/bounces/{bounceid}/dump` - Get bounce dump

## Actions

- create: Send a single email (POST /email)
- create_batch: Send a batch of emails (POST /email/batch)
- create_withtemplate: Send an email using a template (POST /email/withTemplate)
- list: List templates (GET /templates)
- list_bounces: Get bounces (GET /bounces)
- list_deliverystats: Get delivery statistics (GET /deliverystats)
- create_templates: Create a Template (POST /templates)
- update: Update a Template (PUT /templates/{templateIdOrAlias})
- delete: Delete a Template (DELETE /templates/{templateIdOrAlias})
- list_inboundrules: List inbound rule triggers (GET /triggers/inboundrules)
- create_inboundrules: Create an inbound rule trigger (POST /triggers/inboundrules)
- delete_inboundrules: Delete a single trigger (DELETE /triggers/inboundrules/{triggerid})
- get_by_id: Get a single bounce (GET /bounces/{bounceid})
- put_activate: Activate a bounce (PUT /bounces/{bounceid}/activate)
- list_dump: Get bounce dump (GET /bounces/{bounceid}/dump)

## Fields

- `From`: string [REQUIRED for send_email, send_batch] (sender email address)
- `To`: string [REQUIRED for send_email, send_batch, send_template] (recipient email address)
- `Subject`: string [REQUIRED for send_email, send_batch] (email subject)
- `HtmlBody`: string [OPTIONAL for send_email, send_batch] (HTML body content)
- `TextBody`: string [OPTIONAL for send_email, send_batch] (plain text body content)
- `TemplateId`: integer [REQUIRED for send_template] (template ID)
- `TemplateModel`: object [REQUIRED for send_template] (template variables)
- `count`: integer [OPTIONAL for get_bounces] (number of bounces to return)
- `offset`: integer [OPTIONAL for get_bounces] (pagination offset)

## Example Request Bodies

**Send Email:**
```json
{"From": "noreply@example.com", "To": "user@example.com", "Subject": "Hello", "HtmlBody": "<p>Hello from PythonREST!</p>"}
```

**Send Template Email:**
```json
{"TemplateId": 12345, "To": "user@example.com", "TemplateModel": {"name": "Test User"}}
```
