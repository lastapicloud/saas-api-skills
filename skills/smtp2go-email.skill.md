---
name: smtp2go-email
description: Send emails via SMTP2GO. Use when the user mentions smtp2go, email, send
  email, transactional.
version: 1.0.0
skill_type: external
base_url_env: SMTP2GO_BASE_URL
auth_env_var: SMTP2GO_API_KEY
auth_type: header
triggers:
  - smtp2go
  - email
  - send email
  - transactional
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires SMTP2GO_BASE_URL and SMTP2GO_API_KEY environment variables.
---

# Smtp2Go-Email

Send emails via SMTP2GO. Use when the user mentions smtp2go, email, send email, transactional.

## API Endpoints

- **POST** `/v3/email/send` - Send email
- **POST** `/v3/email/send/batch` - Send batch email
- **GET** `/v3/stats/email` - Get email stats
- **GET** `/v3/senders` - List senders
- **POST** `/v3/senders` - Add sender
- **GET** `/v3/domains` - List domains

## Actions

- create: Send email (POST /v3/email/send)
- create_batch: Send batch email (POST /v3/email/send/batch)
- list: Get email stats (GET /v3/stats/email)
- list_senders: List senders (GET /v3/senders)
- create_senders: Add sender (POST /v3/senders)
- list_domains: List domains (GET /v3/domains)

## Fields

- `sender`: string [REQUIRED for send]
- `to`: array [REQUIRED for send]
- `subject`: string [REQUIRED for send]
- `html_body`: string [OPTIONAL]
- `text_body`: string [OPTIONAL]

## Example Request Bodies

**Send Email:**
```json
{"sender": "noreply@example.com", "to": ["user@example.com"], "subject": "Order Confirmation", "html_body": "<h1>Thank you for your order</h1>"}
```

**Add Sender:**
```json
{"email": "notifications@example.com"}
