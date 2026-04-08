---
name: whatsapp-messaging
description: Send messages via WhatsApp Business Cloud API. Use when the user mentions
  whatsapp, message, template, phone.
version: 1.0.0
skill_type: external
base_url_env: WHATSAPP_BASE_URL
auth_env_var: WHATSAPP_ACCESS_TOKEN
auth_type: bearer
triggers:
  - whatsapp
  - message
  - template
  - phone
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires WHATSAPP_BASE_URL and WHATSAPP_ACCESS_TOKEN environment variables.
---

# Whatsapp-Messaging

Send messages via WhatsApp Business Cloud API. Use when the user mentions whatsapp, message, template, phone.

## API Endpoints

- **POST** `/v17.0/{phoneNumberId}/messages` - Send a message
- **GET** `/v17.0/{phoneNumberId}` - Get phone number info
- **GET** `/v17.0/{businessAccountId}/phone_numbers` - List phone numbers
- **POST** `/v17.0/{businessAccountId}/message_templates` - Create a template
- **GET** `/v17.0/{businessAccountId}/message_templates` - List templates
- **DELETE** `/v17.0/{businessAccountId}/message_templates` - Delete a template
- **GET** `/v17.0/{mediaId}` - Get media URL
- **POST** `/v17.0/{phoneNumberId}/media` - Upload media
- **POST** `/users` - Create-User
- **GET** `/users/{UserUsername}` - Get-User
- **PUT** `/users/{UserUsername}` - Update-User
- **DELETE** `/users/{UserUsername}` - Delete-User
- **GET** `/groups` - Get-All-Groups
- **POST** `/groups` - Create-Group
- **PUT** `/groups/{GroupId}` - Update-Group-Info

## Actions

- create: Send a message (POST /v17.0/{phoneNumberId}/messages)
- get_by_id: Get phone number info (GET /v17.0/{phoneNumberId})
- list: List phone numbers (GET /v17.0/{businessAccountId}/phone_numbers)
- create_message_templates: Create a template (POST /v17.0/{businessAccountId}/message_templates)
- list_message_templates: List templates (GET /v17.0/{businessAccountId}/message_templates)
- delete_message_templates: Delete a template (DELETE /v17.0/{businessAccountId}/message_templates)
- get_by_id_v17_0: Get media URL (GET /v17.0/{mediaId})
- create_media: Upload media (POST /v17.0/{phoneNumberId}/media)
- create_users: Create-User (POST /users)
- get_by_id_users: Get-User (GET /users/{UserUsername})
- update: Update-User (PUT /users/{UserUsername})
- delete: Delete-User (DELETE /users/{UserUsername})
- list_groups: Get-All-Groups (GET /groups)
- create_groups: Create-Group (POST /groups)
- update_groups: Update-Group-Info (PUT /groups/{GroupId})

## Fields

- `messaging_product`: string [REQUIRED] ("whatsapp")
- `to`: string [REQUIRED for send] (phone number)
- `type`: string [REQUIRED for send] ("text", "template", "image", "document")
- `text`: object [REQUIRED for text type] with `body`
- `template`: object [REQUIRED for template type] with `name`, `language`

## Example Request Bodies

**Send Text Message:**
```json
{"messaging_product": "whatsapp", "to": "15551234567", "type": "text", "text": {"body": "Hello! Your order has been shipped."}}
```

**Send Template Message:**
```json
{"messaging_product": "whatsapp", "to": "15551234567", "type": "template", "template": {"name": "order_confirmation", "language": {"code": "en_US"}}}
```
