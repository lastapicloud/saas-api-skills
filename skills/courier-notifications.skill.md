---
name: courier-notifications
description: Send notifications via Courier across multiple channels. Use when the
  user mentions courier, notification, send, message, template.
version: 1.0.0
skill_type: external
base_url_env: COURIER_BASE_URL
auth_env_var: COURIER_AUTH_TOKEN
auth_type: bearer
triggers:
  - courier
  - notification
  - send
  - message
  - template
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires COURIER_BASE_URL and COURIER_AUTH_TOKEN environment variables.
---

# Courier-Notifications

Send notifications via Courier across multiple channels. Use when the user mentions courier, notification, send, message, template.

## API Endpoints

- **POST** `/send` - Send a message
- **GET** `/messages` - List messages
- **GET** `/messages/{messageId}` - Get a message
- **GET** `/profiles/{recipientId}` - Get a profile
- **PUT** `/profiles/{recipientId}` - Create/update a profile
- **POST** `/lists` - Create a list
- **GET** `/lists` - List all lists
- **GET** `/brands` - List brands
- **POST** `/brands` - Create a brand
- **GET** `/notifications` - List notification templates

## Actions

- create: Send a message (POST /send)
- list: List messages (GET /messages)
- get_by_id: Get a message (GET /messages/{messageId})
- get_by_id_profiles: Get a profile (GET /profiles/{recipientId})
- update: Create/update a profile (PUT /profiles/{recipientId})
- create_lists: Create a list (POST /lists)
- list_lists: List all lists (GET /lists)
- list_brands: List brands (GET /brands)
- create_brands: Create a brand (POST /brands)
- list_notifications: List notification templates (GET /notifications)

## Fields

- `message`: object [REQUIRED for send] with `to`, `content` or `template`
- `to`: object [REQUIRED] with `email` or `user_id`
- `content`: object [OPTIONAL] with `title`, `body`
- `template`: string [OPTIONAL] (notification template ID)
- `data`: object [OPTIONAL] (template variables)

## Example Request Bodies

**Send Message:**
```json
{"message": {"to": {"email": "user@example.com"}, "content": {"title": "New Notification", "body": "You have a new update."}}}
```

**Create/Update Profile:**
```json
{"email": "user@example.com", "name": "John Doe"}
