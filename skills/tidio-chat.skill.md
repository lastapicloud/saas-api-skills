---
name: tidio-chat
description: 'Manage conversations and contacts via Tidio. Use when the user mentions
  tidio, chat, conversation, contact, visitor, live chat.

  '
version: 1.0.0
skill_type: external
base_url_env: TIDIO_BASE_URL
auth_env_var: TIDIO_API_KEY
auth_type: bearer
triggers:
  - tidio
  - chat
  - conversation
  - contact
  - visitor
  - live chat
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TIDIO_BASE_URL and TIDIO_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Tidio-Chat

Manage conversations and contacts via Tidio. Use when the user mentions tidio, chat, conversation, contact, visitor, live chat.


## API Endpoints

- **GET** `/v1/conversations` - List conversations
- **GET** `/v1/conversations/{id}` - Get conversation
- **POST** `/v1/conversations/{id}/messages` - Send message
- **GET** `/v1/contacts` - List contacts
- **POST** `/v1/contacts` - Create contact
- **GET** `/v1/contacts/{id}` - Get contact
- **PATCH** `/v1/contacts/{id}` - Update contact

## Actions

- list: List conversations (GET /v1/conversations)
- get_by_id: Get conversation (GET /v1/conversations/{id})
- create: Send message (POST /v1/conversations/{id}/messages)
- list_contacts: List contacts (GET /v1/contacts)
- create_contact: Create contact (POST /v1/contacts)
- get_contact: Get contact (GET /v1/contacts/{id})
- update: Update contact (PATCH /v1/contacts/{id})

## Fields

- `message`: string [REQUIRED for send_message] — Message text
- `email`: string [OPTIONAL for create_contact] — Email address
- `name`: string [OPTIONAL] — Display name

## Example Request Bodies

**Send Message:**
```json
{"message": "Hello! How can I help you today?"}
```

**Create Contact:**
```json
{"name": "John Smith", "email": "john@example.com"}

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
