---
name: mailtrap-email
description: Send and test emails via Mailtrap. Use when the user mentions mailtrap,
  email, testing, inbox, transactional.
version: 1.0.0
skill_type: external
base_url_env: MAILTRAP_BASE_URL
auth_env_var: MAILTRAP_API_TOKEN
auth_type: bearer
triggers:
  - mailtrap
  - email
  - testing
  - inbox
  - transactional
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MAILTRAP_BASE_URL and MAILTRAP_API_TOKEN environment variables.
---

# Mailtrap-Email

Send and test emails via Mailtrap. Use when the user mentions mailtrap, email, testing, inbox, transactional.

## API Endpoints

- **POST** `/api/send` - Send email
- **GET** `/api/accounts/{account_id}/inboxes` - List inboxes
- **GET** `/api/accounts/{account_id}/inboxes/{inbox_id}/messages` - List messages
- **GET** `/api/accounts/{account_id}/inboxes/{inbox_id}/messages/{message_id}` - Get message
- **DELETE** `/api/accounts/{account_id}/inboxes/{inbox_id}/messages/{message_id}` - Delete message
- **PATCH** `/api/accounts/{account_id}/inboxes/{inbox_id}/clean` - Clean inbox

## Actions

- create: Send email (POST /api/send)
- list: List inboxes (GET /api/accounts/{account_id}/inboxes)
- list_messages: List messages (GET /api/accounts/{account_id}/inboxes/{inbox_id}/messages)
- get_by_id: Get message (GET /api/accounts/{account_id}/inboxes/{inbox_id}/messages/{message_id})
- delete: Delete message (DELETE /api/accounts/{account_id}/inboxes/{inbox_id}/messages/{message_id})
- patch_clean: Clean inbox (PATCH /api/accounts/{account_id}/inboxes/{inbox_id}/clean)

## Fields

- `from`: object [REQUIRED for send]
- `to`: array [REQUIRED for send]
- `subject`: string [REQUIRED for send]
- `text`: string [OPTIONAL]

## Example Request Bodies

**Send Email:**
```json
{"from": {"email": "noreply@example.com", "name": "Test App"}, "to": [{"email": "tester@example.com"}], "subject": "Test Email", "text": "This is a test email sent via Mailtrap."}
```

**Clean Inbox:**
```json
{}
```
