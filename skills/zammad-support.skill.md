---
name: zammad-support
description: Manage Zammad tickets, users, and organizations. Use when the user mentions
  zammad, ticket, support, helpdesk.
version: 1.0.0
skill_type: external
base_url_env: ZAMMAD_BASE_URL
auth_env_var: ZAMMAD_API_TOKEN
auth_type: bearer
triggers:
  - zammad
  - ticket
  - support
  - helpdesk
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ZAMMAD_BASE_URL and ZAMMAD_API_TOKEN environment variables.
---

# Zammad-Support

Manage Zammad tickets, users, and organizations. Use when the user mentions zammad, ticket, support, helpdesk.

## API Endpoints

- **GET** `/api/v1/tickets` - List tickets
- **GET** `/api/v1/tickets/{ticketId}` - Get a ticket
- **POST** `/api/v1/tickets` - Create a ticket
- **PUT** `/api/v1/tickets/{ticketId}` - Update a ticket
- **DELETE** `/api/v1/tickets/{ticketId}` - Delete a ticket
- **GET** `/api/v1/users` - List users
- **POST** `/api/v1/users` - Create a user
- **GET** `/api/v1/organizations` - List organizations
- **GET** `/api/v1/ticket_articles/by_ticket/{ticketId}` - List ticket articles
- **POST** `/api/v1/ticket_articles` - Create a ticket article

## Actions

- list: List tickets (GET /api/v1/tickets)
- get_by_id: Get a ticket (GET /api/v1/tickets/{ticketId})
- create: Create a ticket (POST /api/v1/tickets)
- update: Update a ticket (PUT /api/v1/tickets/{ticketId})
- delete: Delete a ticket (DELETE /api/v1/tickets/{ticketId})
- list_users: List users (GET /api/v1/users)
- create_users: Create a user (POST /api/v1/users)
- list_organizations: List organizations (GET /api/v1/organizations)
- get_by_id_by_ticket: List ticket articles (GET /api/v1/ticket_articles/by_ticket/{ticketId})
- create_ticket_articles: Create a ticket article (POST /api/v1/ticket_articles)

## Fields

- `title`: string [REQUIRED for create ticket]
- `group`: string [REQUIRED for create ticket]
- `customer_id`: integer [REQUIRED for create ticket]
- `article`: object [REQUIRED for create ticket] with `subject`, `body`, `type`
- `state`: string [OPTIONAL] ("new", "open", "closed")
- `priority`: string [OPTIONAL]

## Example Request Bodies

**Create Ticket:**
```json
{"title": "Login page error", "group": "Support", "customer_id": 42, "article": {"subject": "Login page error", "body": "Users report 500 error on login page.", "type": "note"}, "state": "new"}
```

**Create User:**
```json
{"firstname": "Jane", "lastname": "Doe", "email": "jane@example.com"}
```
