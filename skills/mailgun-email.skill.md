---
name: mailgun-email
description: 'Send emails and manage domains via Mailgun. Use when the user mentions
  mailgun, email, send email, domain, bounce, delivery.

  '
version: 1.0.0
skill_type: external
base_url_env: MAILGUN_BASE_URL
auth_env_var: MAILGUN_API_KEY
auth_type: basic
triggers:
  - mailgun
  - email
  - send email
  - domain
  - bounce
  - delivery
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MAILGUN_BASE_URL and MAILGUN_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Mailgun-Email

Send emails and manage domains via Mailgun. Use when the user mentions mailgun, email, send email, domain, bounce, delivery.


## API Endpoints

- **POST** `/v3/{domain}/messages` - Send email
- **GET** `/v3/{domain}/events` - List events
- **GET** `/v3/domains` - List domains
- **POST** `/v3/domains` - Create domain
- **GET** `/v3/domains/{domain}` - Get domain
- **GET** `/v3/{domain}/bounces` - List bounces
- **GET** `/v3/{domain}/stats/total` - Get stats
- **GET** `/v3/routes` - List routes

## Actions

- create: Send email (POST /v3/{domain}/messages)
- list: List events (GET /v3/{domain}/events)
- list_domains: List domains (GET /v3/domains)
- create_domain: Create domain (POST /v3/domains)
- get_by_id: Get domain (GET /v3/domains/{domain})
- list_bounces: List bounces (GET /v3/{domain}/bounces)
- get_stats: Get stats (GET /v3/{domain}/stats/total)
- list_routes: List routes (GET /v3/routes)

## Fields

- `from`: string [REQUIRED for send] — From
- `to`: string [REQUIRED for send] — To
- `subject`: string [REQUIRED for send] — Subject
- `text`: string [OPTIONAL] — Text content
- `html`: string [OPTIONAL] — Html

## Example Request Bodies

**Send Email:**
```json
{"from": "sender@example.com", "to": "recipient@example.com", "subject": "Order Confirmation", "text": "Your order #12345 has been confirmed."}
```

**Create Domain:**
```json
{"name": "mail.example.com"}
```

## Response

**Domain object:**
- `id`: string — Unique domain identifier
- `name`: string — Domain name or title
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
