---
name: mailgun-email
description: Send emails and manage domains via Mailgun. Use when the user mentions
  mailgun, email, send email, domain, bounce, delivery.
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
- create_domains: Create domain (POST /v3/domains)
- get_by_id: Get domain (GET /v3/domains/{domain})
- list_bounces: List bounces (GET /v3/{domain}/bounces)
- list_total: Get stats (GET /v3/{domain}/stats/total)
- list_routes: List routes (GET /v3/routes)

## Fields

- `from`: string [REQUIRED for send]
- `to`: string [REQUIRED for send]
- `subject`: string [REQUIRED for send]
- `text`: string [OPTIONAL]
- `html`: string [OPTIONAL]

## Example Request Bodies

**Send Email:**
```json
{"from": "sender@example.com", "to": "recipient@example.com", "subject": "Order Confirmation", "text": "Your order #12345 has been confirmed."}
```

**Create Domain:**
```json
{"name": "mail.example.com"}
```
