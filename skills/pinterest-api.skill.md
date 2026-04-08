---
name: pinterest-api
description: Manage pins and boards via Pinterest API. Use when the user mentions
  pinterest, pin, board, social media, image.
version: 1.0.0
skill_type: external
base_url_env: PINTEREST_BASE_URL
auth_env_var: PINTEREST_ACCESS_TOKEN
auth_type: bearer
triggers:
  - pinterest
  - pin
  - board
  - social media
  - image
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires PINTEREST_BASE_URL and PINTEREST_ACCESS_TOKEN environment
  variables.
---

# Pinterest-Api

Manage pins and boards via Pinterest API. Use when the user mentions pinterest, pin, board, social media, image.

## API Endpoints

- **GET** `/v5/pins` - List pins
- **POST** `/v5/pins` - Create pin
- **GET** `/v5/pins/{pin_id}` - Get pin
- **DELETE** `/v5/pins/{pin_id}` - Delete pin
- **GET** `/v5/boards` - List boards
- **POST** `/v5/boards` - Create board
- **GET** `/v5/user_account` - Get user account
- **GET** `/v5/user_account/analytics` - Get analytics

## Actions

- list: List pins (GET /v5/pins)
- create: Create pin (POST /v5/pins)
- get_by_id: Get pin (GET /v5/pins/{pin_id})
- delete: Delete pin (DELETE /v5/pins/{pin_id})
- list_boards: List boards (GET /v5/boards)
- create_boards: Create board (POST /v5/boards)
- list_user_account: Get user account (GET /v5/user_account)
- list_analytics: Get analytics (GET /v5/user_account/analytics)

## Fields

- `board_id`: string [REQUIRED for create]
- `media_source`: object [REQUIRED for create]
- `title`: string [OPTIONAL]

## Example Request Bodies

**Create Pin:**
```json
{"board_id": "board-12345", "media_source": {"source_type": "image_url", "url": "https://example.com/recipe.jpg"}, "title": "Easy Pasta Recipe"}
```

**Create Board:**
```json
{"name": "Travel Inspiration", "description": "Dream destinations and travel tips"}
```
