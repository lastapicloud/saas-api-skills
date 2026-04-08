---
name: helpscout-support
description: Manage conversations and customers via Help Scout. Use when the user
  mentions help scout, helpscout, conversation, mailbox, customer, support.
version: 1.0.0
skill_type: external
base_url_env: HELPSCOUT_BASE_URL
auth_env_var: HELPSCOUT_ACCESS_TOKEN
auth_type: bearer
triggers:
  - help scout
  - helpscout
  - conversation
  - mailbox
  - customer
  - support
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires HELPSCOUT_BASE_URL and HELPSCOUT_ACCESS_TOKEN environment
  variables.
---

# Helpscout-Support

Manage conversations and customers via Help Scout. Use when the user mentions help scout, helpscout, conversation, mailbox, customer, support.

## API Endpoints

- **GET** `/v2/conversations` - List conversations
- **POST** `/v2/conversations` - Create conversation
- **GET** `/v2/conversations/{id}` - Get conversation
- **PATCH** `/v2/conversations/{id}` - Update conversation
- **DELETE** `/v2/conversations/{id}` - Delete conversation
- **GET** `/v2/customers` - List customers
- **POST** `/v2/customers` - Create customer
- **GET** `/v2/mailboxes` - List mailboxes

## Actions

- list: List conversations (GET /v2/conversations)
- create: Create conversation (POST /v2/conversations)
- get_by_id: Get conversation (GET /v2/conversations/{id})
- update: Update conversation (PATCH /v2/conversations/{id})
- delete: Delete conversation (DELETE /v2/conversations/{id})
- list_customers: List customers (GET /v2/customers)
- create_customers: Create customer (POST /v2/customers)
- list_mailboxes: List mailboxes (GET /v2/mailboxes)

## Fields

- `subject`: string [REQUIRED for create]
- `customer`: object [REQUIRED for create]
- `mailboxId`: integer [REQUIRED for create]
- `type`: string [REQUIRED for create]
- `threads`: array [REQUIRED for create]

## Example Request Bodies

**Create Conversation:**
```json
{"subject": "Billing question", "customer": {"email": "jane@example.com"}, "mailboxId": 12345, "type": "email", "threads": [{"type": "customer", "customer": {"email": "jane@example.com"}, "text": "I have a question about my invoice."}]}
```

**Create Customer:**
```json
{"firstName": "Jane", "lastName": "Doe", "emails": [{"type": "work", "value": "jane@example.com"}]}
```
