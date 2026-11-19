---
name: freshdesk-support
description: 'Manage tickets, contacts, and agents in Freshdesk. Use when the user
  mentions freshdesk, ticket, support, helpdesk, contact, agent.

  '
version: 1.0.0
skill_type: external
base_url_env: FRESHDESK_BASE_URL
auth_env_var: FRESHDESK_API_KEY
auth_type: basic
triggers:
  - freshdesk
  - ticket
  - support
  - helpdesk
  - contact
  - agent
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FRESHDESK_BASE_URL and FRESHDESK_API_KEY environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Freshdesk-Support

Manage tickets, contacts, and agents in Freshdesk. Use when the user mentions freshdesk, ticket, support, helpdesk, contact, agent.


## API Endpoints

- **GET** `/tickets` - List tickets
- **POST** `/tickets` - Create a ticket
- **GET** `/tickets/{ticket_id}` - Get a ticket
- **PUT** `/tickets/{ticket_id}` - Update a ticket
- **GET** `/contacts` - List contacts
- **POST** `/contacts` - Create a contact
- **GET** `/agents` - List agents
- **GET** `/tickets/{ticket_id}/conversations` - List ticket conversations
- **POST** `/api/v2/tickets`
- **POST** `/api/v2/tickets/outbound_email` - Note:
- **GET** `/api/v2/tickets/` - Use 'include' to embed additional details in the response. Each include will consume an additional credit. For example
- **GET** `/api/v2/tickets` - Use filters to view only specific tickets (those which match the criteria that you choose). By default, only tickets
- **GET** `/api/v2/search/tickets` - Use custom ticket fields that you have created in your account to filter through the tickets and get a list of tickets
- **PUT** `/api/v2/tickets/` - Note:
- **POST** `/api/v2/tickets/bulk_update` - Note:

## Actions

- list: List tickets (GET /tickets)
- create: Create a ticket (POST /tickets)
- get_by_id: Get a ticket (GET /tickets/{ticket_id})
- update: Update a ticket (PUT /tickets/{ticket_id})
- list_contacts: List contacts (GET /contacts)
- create_contact: Create a contact (POST /contacts)
- list_agents: List agents (GET /agents)
- list_ticket_conversations: List ticket conversations (GET /tickets/{ticket_id}/conversations)
- create_tickets: POST /api/v2/tickets (POST /api/v2/tickets)
- create_note: Note: (POST /api/v2/tickets/outbound_email)
- get_use_include_embed_additional: Use 'include' to embed additional details in the response. Each include will con (GET /api/v2/tickets/)
- get_use_filters_view_only: Use filters to view only specific tickets (those which match the criteria that y (GET /api/v2/tickets)
- get_use_custom_ticket_fields: Use custom ticket fields that you have created in your account to filter through (GET /api/v2/search/tickets)
- put_tickets: Note: (PUT /api/v2/tickets/)
- create_bulk_update: Note: (POST /api/v2/tickets/bulk_update)

## Fields

- `ticket_id`: integer [REQUIRED for get/update ticket, list_conversations] (ticket ID) — Ticket unique identifier
- `subject`: string [REQUIRED for create_ticket] (ticket subject) — Subject
- `description`: string [REQUIRED for create_ticket] (ticket description HTML) — Human-readable description
- `email`: string [REQUIRED for create_ticket, create_contact] (requester email) — Email address
- `priority`: integer [OPTIONAL for create_ticket] (1=low, 2=medium, 3=high, 4=urgent) — Priority level
- `status`: integer [OPTIONAL for update_ticket] (2=open, 3=pending, 4=resolved, 5=closed) — Current status
- `type`: string [OPTIONAL for create_ticket] (ticket type: Question, Incident, Problem, etc.) — Resource type
- `name`: string [OPTIONAL for create_contact] (contact name) — Display name
- `phone`: string [OPTIONAL for create_contact] (contact phone) — Phone number
- `page`: integer [OPTIONAL] (page number) — Page number
- `per_page`: integer [OPTIONAL] (results per page, max 100) — Per page number

## Example Request Bodies

**Create Ticket:**
```json
{"subject": "Login issue", "description": "Unable to log in to the dashboard", "email": "user@example.com", "priority": 3, "status": 2}
```

**Update Ticket:**
```json
{"status": 4, "priority": 2}
```

**Create Contact:**
```json
{"name": "Jane Doe", "email": "jane@example.com", "phone": "+1234567890"}
```

## Response

**Ticket object:**
- `id`: string — Unique ticket identifier
- `name`: string — Ticket name or title
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
