---
name: zendesk-tickets
description: Manage support tickets and users in Zendesk. Use when the user mentions
  zendesk, ticket, support, customer, helpdesk.
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
- list_tickets: Get a ticket (GET /tickets/{ticketId}.json)
- update_tickets: Update a ticket (PUT /tickets/{ticketId}.json)
- search: Search tickets (GET /search.json)
- list_users_json: List users (GET /users.json)
- update_tickets_6: Add a comment to a ticket (PUT /tickets/{ticketId}.json)
- list_tickets_2: For more information about custom ticket statuses and status categories, see Cre (GET /api/v2/tickets)
- list_tickets_3: Returns a list of tickets for a specific organization. (GET /api/v2/organizations/{organization_id}/tickets)
- list_count: Returns an approximate count of tickets for a specific organization. If the coun (GET /api/v2/organizations/{organization_id}/tickets/count)
- list_recent: If an agent with restricted access to tickets makes a request to the api/v2/tick (GET /api/v2/tickets/recent)
- list_count_2: Returns an approximate count of tickets in the account. If the count exceeds 100 (GET /api/v2/tickets/count)
- get_by_id: Returns a number of ticket properties, but doesn't include the full comment thre (GET /api/v2/tickets/{ticket_id})
- list_show_many: Accepts a comma-separated list of ticket ids to return. (GET /api/v2/tickets/show_many)
- create_tickets: Takes a ticket object that specifies the ticket properties. The only required pr (POST /api/v2/tickets)

## Fields

- `ticketId`: string [REQUIRED for get_ticket, update_ticket, add_comment] (ticket ID)
- `subject`: string [REQUIRED for create_ticket] (ticket subject)
- `description`: string [OPTIONAL for create_ticket] (ticket description)
- `priority`: string [OPTIONAL] (urgent, high, normal, low)
- `status`: string [OPTIONAL] (new, open, pending, hold, solved, closed)
- `assignee_id`: integer [OPTIONAL] (agent ID to assign)
- `query`: string [REQUIRED for search_tickets] (search query)
- `comment`: object [REQUIRED for add_comment] (comment body and public flag)

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
