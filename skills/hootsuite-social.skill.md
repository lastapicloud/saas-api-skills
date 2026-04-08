---
name: hootsuite-social
description: Manage social media posts and profiles via Hootsuite. Use when the user
  mentions hootsuite, social media, post, schedule, profile, publish.
version: 1.0.0
skill_type: external
base_url_env: HOOTSUITE_BASE_URL
auth_env_var: HOOTSUITE_ACCESS_TOKEN
auth_type: bearer
triggers:
  - hootsuite
  - social media
  - post
  - schedule
  - profile
  - publish
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires HOOTSUITE_BASE_URL and HOOTSUITE_ACCESS_TOKEN environment
  variables.
---

# Hootsuite-Social

Manage social media posts and profiles via Hootsuite. Use when the user mentions hootsuite, social media, post, schedule, profile, publish.

## API Endpoints

- **GET** `/v1/socialProfiles` - List profiles
- **GET** `/v1/messages` - List messages
- **POST** `/v1/messages` - Create message
- **GET** `/v1/messages/{messageId}` - Get message
- **DELETE** `/v1/messages/{messageId}` - Delete message
- **GET** `/v1/media` - List media
- **POST** `/v1/media` - Upload media
- **GET** `/v1/me` - Get current user

## Actions

- list: List profiles (GET /v1/socialProfiles)
- list_messages: List messages (GET /v1/messages)
- create: Create message (POST /v1/messages)
- get_by_id: Get message (GET /v1/messages/{messageId})
- delete: Delete message (DELETE /v1/messages/{messageId})
- list_media: List media (GET /v1/media)
- create_media: Upload media (POST /v1/media)
- list_me: Get current user (GET /v1/me)

## Fields

- `text`: string [REQUIRED for create]
- `socialProfileIds`: array [REQUIRED for create]
- `scheduledSendTime`: string [OPTIONAL]

## Example Request Bodies

**Create Message:**
```json
{"text": "Check out our latest blog post!", "socialProfileIds": ["123456789"], "scheduledSendTime": "2024-03-15T14:00:00Z"}
```

**Upload Media:**
```json
{"url": "https://example.com/image.png", "mimeType": "image/png"}
```
