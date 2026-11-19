---
name: zendesk-tickets
description: 'Manage support tickets and users in Zendesk. Use when the user mentions
  zendesk, ticket, support, customer, helpdesk.

  '
version: 1.0.0
skill_type: external
base_url_env: ZENDESK_BASE_URL
auth_env_var: ZENDESK_API_TOKEN
auth_user_env: ZENDESK_EMAIL
auth_type: basic
triggers:
  - zendesk
  - ticket
  - support
  - customer
  - helpdesk
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ZENDESK_BASE_URL and ZENDESK_API_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: false
  idempotentHint: false
---

# Zendesk-Tickets

Manage support tickets and users in Zendesk. Use when the user mentions zendesk, ticket, support, customer, helpdesk.


## API Endpoints

- **GET** `/tickets.json` - List tickets
- **POST** `/tickets.json` - Create a ticket
- **GET** `/tickets/{ticketId}.json` - Get a ticket
- **PUT** `/tickets/{ticketId}.json` - Update a ticket
- **GET** `/search.json` - Search tickets
- **GET** `/users.json` - List users
- **PUT** `/tickets/{ticketId}.json` - Add a comment to a ticket
- **GET** `/api/v2/tickets` - For more information about custom ticket statuses and status categories, see Creating custom ticket statuses.
- **GET** `/api/v2/organizations/{organization_id}/tickets` - Returns a list of tickets for a specific organization.
- **GET** `/api/v2/organizations/{organization_id}/tickets/count` - Returns an approximate count of tickets for a specific organization. If the count exceeds 100,000, it is updated every
- **GET** `/api/v2/tickets/recent` - If an agent with restricted access to tickets makes a request to the api/v2/tickets endpoint, the endpoint returns only
- **GET** `/api/v2/tickets/count` - Returns an approximate count of tickets in the account. If the count exceeds 100,000, it is updated every 24 hours.
- **GET** `/api/v2/tickets/{ticket_id}` - Returns a number of ticket properties, but doesn't include the full comment thread. The initial comment is available in
- **GET** `/api/v2/tickets/show_many` - Accepts a comma-separated list of ticket ids to return.
- **POST** `/api/v2/tickets` - Takes a ticket object that specifies the ticket properties. The only required property is comment. See Ticket Comments.

## Actions

- list: List tickets (GET /tickets.json)
- create: Create a ticket (POST /tickets.json)
- get_ticket: Get a ticket (GET /tickets/{ticketId}.json)
- update_tickets: Update a ticket (PUT /tickets/{ticketId}.json)
- search: Search tickets (GET /search.json)
- list_users: List users (GET /users.json)
- add_comment_ticket: Add a comment to a ticket (PUT /tickets/{ticketId}.json)
- get_more_information_about_custom: For more information about custom ticket statuses and status categories, see Cre (GET /api/v2/tickets)
- get_list_tickets_specific: Returns a list of tickets for a specific organization. (GET /api/v2/organizations/{organization_id}/tickets)
- get_approximate_count_tickets: Returns an approximate count of tickets for a specific organization. If the coun (GET /api/v2/organizations/{organization_id}/tickets/count)
- get_if_agent_restricted_access: If an agent with restricted access to tickets makes a request to the api/v2/tick (GET /api/v2/tickets/recent)
- list_count: Returns an approximate count of tickets in the account. If the count exceeds 100 (GET /api/v2/tickets/count)
- get_by_id: Returns a number of ticket properties, but doesn't include the full comment thre (GET /api/v2/tickets/{ticket_id})
- get_accepts_commaseparated_list_ticket: Accepts a comma-separated list of ticket ids to return. (GET /api/v2/tickets/show_many)
- create_takes_ticket_object_that: Takes a ticket object that specifies the ticket properties. The only required pr (POST /api/v2/tickets)

## Fields

- `ticketId`: string [REQUIRED for get_ticket, update_ticket, add_comment] (ticket ID) — Ticket unique identifier
- `subject`: string [REQUIRED for create_ticket] (ticket subject) — Subject
- `description`: string [OPTIONAL for create_ticket] (ticket description) — Human-readable description
- `priority`: string [OPTIONAL] (urgent, high, normal, low) — Priority level
- `status`: string [OPTIONAL] (new, open, pending, hold, solved, closed) — Current status
- `assignee_id`: integer [OPTIONAL] (agent ID to assign) — Assignee unique identifier
- `query`: string [REQUIRED for search_tickets] (search query) — Search or filter query
- `comment`: object [REQUIRED for add_comment] (comment body and public flag) — Comment configuration

## Example Request Bodies

**Create Ticket:**
```json
{"ticket": {"subject": "Cannot log in", "description": "User reports 500 error on login page", "priority": "high"}}
```

**Update Ticket:**
```json
{"ticket": {"status": "solved", "assignee_id": 12345}}
```

**Add Comment:**
```json
{"ticket": {"comment": {"body": "We have deployed a fix for this issue.", "public": true}}}
```

**Search Tickets (Query Params):**
Query parameter: `query=type:ticket+status:open+priority:high`

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
