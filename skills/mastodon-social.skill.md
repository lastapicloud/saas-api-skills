---
name: mastodon-social
description: Post statuses and manage accounts via Mastodon. Use when the user mentions
  mastodon, toot, status, fediverse, social media, timeline.
version: 1.0.0
skill_type: external
base_url_env: MASTODON_BASE_URL
auth_env_var: MASTODON_ACCESS_TOKEN
auth_type: bearer
triggers:
  - mastodon
  - toot
  - status
  - fediverse
  - social media
  - timeline
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MASTODON_BASE_URL and MASTODON_ACCESS_TOKEN environment variables.
---

# Mastodon-Social

Post statuses and manage accounts via Mastodon. Use when the user mentions mastodon, toot, status, fediverse, social media, timeline.

## API Endpoints

- **GET** `/api/v2/instance` - Get instance info
- **GET** `/api/v1/trends` - Get trending tags
- **GET** `/api/v1/timelines/home` - Get home timeline
- **GET** `/api/v1/timelines/public` - Get public timeline
- **POST** `/api/v1/statuses` - Create status
- **GET** `/api/v1/statuses/{id}` - Get status
- **DELETE** `/api/v1/statuses/{id}` - Delete status
- **POST** `/api/v1/statuses/{id}/favourite` - Favourite status
- **POST** `/api/v1/statuses/{id}/reblog` - Boost status
- **GET** `/api/v1/accounts/verify_credentials` - Get current account
- **GET** `/api/v1/accounts/search` - Search accounts
- **PATCH** `/api/v1/accounts/update_credentials` - Update account
- **POST** `/api/v1/accounts` - Create account
- **GET** `/api/v2/search` - Search content
- **GET** `/api/v1/bookmarks` - Get bookmarks
- **GET** `/api/v1/favourites` - Get favourites
- **GET** `/api/v1/notifications` - Get notifications

## Actions

- get_instance: Get instance info (GET /api/v2/instance)
- list_trends: Get trending tags (GET /api/v1/trends)
- list: Get home timeline (GET /api/v1/timelines/home)
- list_public: Get public timeline (GET /api/v1/timelines/public)
- create: Create status (POST /api/v1/statuses)
- get_by_id: Get status (GET /api/v1/statuses/{id})
- delete: Delete status (DELETE /api/v1/statuses/{id})
- create_favourite: Favourite status (POST /api/v1/statuses/{id}/favourite)
- create_reblog: Boost status (POST /api/v1/statuses/{id}/reblog)
- list_verify_credentials: Get current account (GET /api/v1/accounts/verify_credentials)
- search: Search accounts (GET /api/v1/accounts/search)
- patch_update_credentials: Update account (PATCH /api/v1/accounts/update_credentials)
- create_accounts: Create account (POST /api/v1/accounts)
- search_content: Search content (GET /api/v2/search)
- list_bookmarks: Get bookmarks (GET /api/v1/bookmarks)
- list_favourites: Get favourites (GET /api/v1/favourites)
- list_notifications: Get notifications (GET /api/v1/notifications)

## Fields

- `status`: string [REQUIRED for create status] (status content)
- `visibility`: string [OPTIONAL] (public, unlisted, private, direct)
- `media_ids`: array [OPTIONAL] (attached media IDs)
- `id`: string [REQUIRED for get/delete status] (status ID)
- `account_id`: string [REQUIRED for get/update account] (account ID)
- `display_name`: string [OPTIONAL for update_credentials] (display name)
- `note`: string [OPTIONAL for update_credentials] (bio note)
- `locked`: boolean [OPTIONAL] (whether account is locked)
- `query`: string [OPTIONAL for search] (search query)

## Example Request Bodies

**Create Status:**
```json
{"status": "Hello Fediverse! Excited to be here.", "visibility": "public"}
```

**Update Credentials:**
```json
{"display_name": "Jane Doe", "note": "Software engineer and open source enthusiast", "locked": false}
```

**Search Content:**
```json
{"q": "mastodon", "type": "accounts"}
```
