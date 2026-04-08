---
name: front-inbox
description: Manage conversations, contacts, and inboxes via Front. Use when the user
  mentions front, inbox, conversation, contact, message, email.
version: 1.0.0
skill_type: external
base_url_env: FRONT_BASE_URL
auth_env_var: FRONT_API_TOKEN
auth_type: bearer
triggers:
  - front
  - inbox
  - conversation
  - contact
  - message
  - email
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FRONT_BASE_URL and FRONT_API_TOKEN environment variables.
---

# Front-Inbox

Manage conversations, contacts, and inboxes via Front. Use when the user mentions front, inbox, conversation, contact, message, email.

## API Endpoints

- **GET** `/conversations` - List conversations
- **GET** `/conversations/{conversation_id}` - Get conversation
- **POST** `/conversations/{conversation_id}/messages` - Reply to conversation
- **GET** `/contacts` - List contacts
- **POST** `/contacts` - Create contact
- **GET** `/contacts/{contact_id}` - Get contact
- **GET** `/inboxes` - List inboxes
- **GET** `/teammates` - List teammates
- **POST** `/providers/Microsoft.Network/checkFrontDoorNameAvailability` - Check the availability of a Front Door resource name.
- **GET** `/subscriptions/{subscriptionId}/providers/Microsoft.Network/frontDoors` - Lists all of the Front Doors within an Azure subscription.
- **POST** `/subscriptions/{subscriptionId}/providers/Microsoft.Network/checkFrontDoorNameAvailability` - Check the availability of a Front Door subdomain.
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/frontDoors` - Lists all of the Front Doors within a resource group under a subscription.
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/frontDoors/{frontDoorName}` - Gets a Front Door with the specified Front Door name under the specified subscription and resource group.
- **PUT** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/frontDoors/{frontDoorName}` - Creates a new Front Door with a Front Door name under the specified subscription and resource group.
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/frontDoors/{frontDoorName}/frontendEndpoints` - Lists all of the frontend endpoints within a Front Door.

## Actions

- list: List conversations (GET /conversations)
- get_by_id: Get conversation (GET /conversations/{conversation_id})
- create: Reply to conversation (POST /conversations/{conversation_id}/messages)
- list_contacts: List contacts (GET /contacts)
- create_contacts: Create contact (POST /contacts)
- get_by_id_contacts: Get contact (GET /contacts/{contact_id})
- list_inboxes: List inboxes (GET /inboxes)
- list_teammates: List teammates (GET /teammates)
- create_checkfrontdoornameavailability: Check the availability of a Front Door resource name. (POST /providers/Microsoft.Network/checkFrontDoorNameAvailability)
- list_frontdoors: Lists all of the Front Doors within an Azure subscription. (GET /subscriptions/{subscriptionId}/providers/Microsoft.Network/frontDoors)
- create_checkfrontdoornameavailability_2: Check the availability of a Front Door subdomain. (POST /subscriptions/{subscriptionId}/providers/Microsoft.Network/checkFrontDoorNameAvailability)
- list_frontdoors_2: Lists all of the Front Doors within a resource group under a subscription. (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/frontDoors)
- get_by_id_frontdoors: Gets a Front Door with the specified Front Door name under the specified subscri (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/frontDoors/{frontDoorName})
- update: Creates a new Front Door with a Front Door name under the specified subscription (PUT /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/frontDoors/{frontDoorName})
- list_frontendendpoints: Lists all of the frontend endpoints within a Front Door. (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/frontDoors/{frontDoorName}/frontendEndpoints)

## Fields

- `body`: string [REQUIRED for reply]
- `handles`: array [REQUIRED for create_contact]
- `name`: string [OPTIONAL]

## Example Request Bodies

**Reply to Conversation:**
```json
{"body": "Thank you for reaching out. We will look into this and get back to you shortly."}
```

**Create Contact:**
```json
{"handles": [{"handle": "customer@example.com", "source": "email"}], "name": "Jane Smith"}
```
