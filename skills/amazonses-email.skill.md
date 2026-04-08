---
name: amazonses-email
description: Send emails via Amazon SES. Use when the user mentions amazon ses, SES,
  email, send email, aws email.
version: 1.0.0
skill_type: external
base_url_env: AMAZON_SES_BASE_URL
auth_env_var: AMAZON_SES_BASE_URL
auth_type: header
triggers:
  - amazon ses
  - SES
  - email
  - send email
  - aws email
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires AMAZON_SES_BASE_URL and AMAZON_SES_BASE_URL environment variables.
---

# Amazonses-Email

Send emails via Amazon SES. Use when the user mentions amazon ses, SES, email, send email, aws email.

## API Endpoints

- **POST** `/v2/email/outbound-emails` - Send an email
- **GET** `/v2/email/identities` - List email identities
- **POST** `/v2/email/identities` - Create an email identity
- **GET** `/v2/email/identities/{emailIdentity}` - Get an identity
- **DELETE** `/v2/email/identities/{emailIdentity}` - Delete an identity
- **GET** `/v2/email/configuration-sets` - List configuration sets
- **GET** `/v2/email/templates` - List email templates
- **POST** `/v2/email/templates` - Create a template
- **GET** `/v2/email/suppression/addresses` - List suppressed addresses
- **GET** `/v2/email/account` - Get account info

## Actions

- create: Send an email (POST /v2/email/outbound-emails)
- list: List email identities (GET /v2/email/identities)
- create_identities: Create an email identity (POST /v2/email/identities)
- get_by_id: Get an identity (GET /v2/email/identities/{emailIdentity})
- delete: Delete an identity (DELETE /v2/email/identities/{emailIdentity})
- list_configuration_sets: List configuration sets (GET /v2/email/configuration-sets)
- list_templates: List email templates (GET /v2/email/templates)
- create_templates: Create a template (POST /v2/email/templates)
- list_addresses: List suppressed addresses (GET /v2/email/suppression/addresses)
- list_account: Get account info (GET /v2/email/account)

## Fields

- `FromEmailAddress`: string [REQUIRED for send]
- `Destination`: object [REQUIRED] with `ToAddresses` array
- `Content`: object [REQUIRED] with `Simple` or `Template` or `Raw`

## Example Request Bodies

**Send Email:**
```json
{"FromEmailAddress": "noreply@example.com", "Destination": {"ToAddresses": ["user@example.com"]}, "Content": {"Simple": {"Subject": {"Data": "Order Confirmation"}, "Body": {"Text": {"Data": "Your order has been placed."}}}}}
```

**Create Email Template:**
```json
{"TemplateName": "welcome_email", "SubjectPart": "Welcome, {{name}}!", "HtmlPart": "<h1>Hello {{name}}</h1>"}
```
