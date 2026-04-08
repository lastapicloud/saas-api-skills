---
name: novu-notifications
description: Trigger notification workflows and manage subscribers via the Novu API.
  Use when the user mentions novu, notification, notify, subscriber, workflow, trigger.
version: 1.0.0
skill_type: external
base_url_env: NOVU_BASE_URL
auth_env_var: NOVU_API_KEY
auth_type: header
triggers:
  - novu
  - notification
  - notify
  - subscriber
  - workflow
  - trigger
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires NOVU_BASE_URL and NOVU_API_KEY environment variables.
---

# Novu-Notifications

Trigger notification workflows and manage subscribers via the Novu API. Use when the user mentions novu, notification, notify, subscriber, workflow, trigger.

## API Endpoints

- **POST** `/events/trigger` - Trigger a notification workflow
- **GET** `/subscribers` - List subscribers
- **POST** `/subscribers` - Create a subscriber
- **GET** `/subscribers/{subscriberId}` - Get a subscriber
- **PATCH** `/subscribers/{subscriberId}` - Update a subscriber
- **DELETE** `/subscribers/{subscriberId}` - Delete a subscriber
- **GET** `/workflows` - List workflows
- **POST** `/workflows` - Create a workflow
- **PATCH** `/workflows/{workflowId}` - Update a workflow
- **DELETE** `/workflows/{workflowId}` - Delete a workflow
- **GET** `/messages` - List messages
- **GET** `/messages/{messageId}` - Get a message
- **DELETE** `/messages/{messageId}` - Delete a message
- **POST** `/events/trigger/broadcast` - Trigger broadcast to all

## Actions

- create: Trigger a notification workflow (POST /events/trigger)
- create_broadcast: Trigger broadcast to all (POST /events/trigger/broadcast)
- list: List subscribers (GET /subscribers)
- create_subscribers: Create a subscriber (POST /subscribers)
- get_by_id: Get a subscriber (GET /subscribers/{subscriberId})
- update: Update a subscriber (PATCH /subscribers/{subscriberId})
- delete: Delete a subscriber (DELETE /subscribers/{subscriberId})
- list_workflows: List workflows (GET /workflows)
- create_workflows: Create a workflow (POST /workflows)
- update_workflows: Update a workflow (PATCH /workflows/{workflowId})
- delete_workflows: Delete a workflow (DELETE /workflows/{workflowId})
- list_messages: List messages (GET /messages)
- get_by_id_messages: Get a message (GET /messages/{messageId})
- delete_messages: Delete a message (DELETE /messages/{messageId})

## Fields

- `name`: string [REQUIRED for trigger_workflow] (workflow trigger identifier)
- `to`: object [REQUIRED for trigger_workflow] (subscriber target with subscriberId)
- `payload`: object [OPTIONAL for trigger_workflow] (notification payload data)
- `subscriberId`: string [REQUIRED for create_subscriber] (unique subscriber identifier)
- `email`: string [OPTIONAL for create_subscriber] (subscriber email)
- `firstName`: string [OPTIONAL for create_subscriber] (subscriber first name)
- `lastName`: string [OPTIONAL for create_subscriber] (subscriber last name)

## Example Request Bodies

**Trigger Workflow:**
```json
{"name": "welcome-email", "to": {"subscriberId": "user-123"}, "payload": {"message": "Hello from PythonREST!"}}
```

**Create Subscriber:**
```json
{"subscriberId": "user-123", "email": "user@example.com", "firstName": "Test", "lastName": "User"}
```
