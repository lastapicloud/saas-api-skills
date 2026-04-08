---
name: facebook-pages
description: Manage Facebook pages, posts, and insights. Use when the user mentions
  facebook, page, post, social, insight.
version: 1.0.0
skill_type: external
base_url_env: FACEBOOK_BASE_URL
auth_env_var: FACEBOOK_ACCESS_TOKEN
auth_type: bearer
triggers:
  - facebook
  - page
  - post
  - social
  - insight
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires FACEBOOK_BASE_URL and FACEBOOK_ACCESS_TOKEN environment variables.
---

# Facebook-Pages

Manage Facebook pages, posts, and insights. Use when the user mentions facebook, page, post, social, insight.

## API Endpoints

- **GET** `/v18.0/me/accounts` - List pages
- **GET** `/v18.0/{pageId}` - Get a page
- **POST** `/v18.0/{pageId}/feed` - Create a post
- **GET** `/v18.0/{pageId}/feed` - List posts
- **GET** `/v18.0/{postId}` - Get a post
- **DELETE** `/v18.0/{postId}` - Delete a post
- **GET** `/v18.0/{pageId}/insights` - Get page insights
- **POST** `/v18.0/{postId}/comments` - Add a comment
- **GET** `/v18.0/{postId}/comments` - List comments
- **GET** `/v18.0/me` - Get current user

## Actions

- list: List pages (GET /v18.0/me/accounts)
- get_by_id: Get a page (GET /v18.0/{pageId})
- create: Create a post (POST /v18.0/{pageId}/feed)
- list_feed: List posts (GET /v18.0/{pageId}/feed)
- get_by_id_v18_0: Get a post (GET /v18.0/{postId})
- delete: Delete a post (DELETE /v18.0/{postId})
- list_insights: Get page insights (GET /v18.0/{pageId}/insights)
- create_comments: Add a comment (POST /v18.0/{postId}/comments)
- list_comments: List comments (GET /v18.0/{postId}/comments)
- list_me: Get current user (GET /v18.0/me)

## Fields

- `message`: string [REQUIRED for create post]
- `link`: string [OPTIONAL for post]
- `metric`: string [OPTIONAL for insights]
- `period`: string [OPTIONAL] ("day", "week", "days_28", "month")

## Example Request Bodies

**Create a Post:**
```json
{
  "message": "Excited to announce our new product launch!",
  "link": "https://example.com/product"
}
```

**Add a Comment:**
```json
{
  "message": "Great post! Looking forward to the launch."
}
```
