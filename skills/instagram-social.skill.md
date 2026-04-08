---
name: instagram-social
description: Manage Instagram Business media and insights. Use when the user mentions
  instagram, media, post, story, social, reel.
version: 1.0.0
skill_type: external
base_url_env: INSTAGRAM_BASE_URL
auth_env_var: INSTAGRAM_ACCESS_TOKEN
auth_type: bearer
triggers:
  - instagram
  - media
  - post
  - story
  - social
  - reel
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires INSTAGRAM_BASE_URL and INSTAGRAM_ACCESS_TOKEN environment
  variables.
---

# Instagram-Social

Manage Instagram Business media and insights. Use when the user mentions instagram, media, post, story, social, reel.

## API Endpoints

- **GET** `/v18.0/{userId}/media` - List media
- **GET** `/v18.0/{mediaId}` - Get media details
- **POST** `/v18.0/{userId}/media` - Create media container
- **POST** `/v18.0/{userId}/media_publish` - Publish media
- **GET** `/v18.0/{mediaId}/comments` - List comments
- **POST** `/v18.0/{mediaId}/comments` - Reply to comment
- **GET** `/v18.0/{userId}/insights` - Get account insights
- **GET** `/v18.0/{mediaId}/insights` - Get media insights
- **GET** `/v18.0/{userId}/stories` - List stories
- **GET** `/v18.0/me` - Get current user
- **GET** `/v1/media/search` - Search for media in a given area.
- **DELETE** `/v1/media/{media-id}/comments/{comment-id}` - Remove a comment.
- **POST** `/v1/media/{media-id}/comments` - Create a comment on a media object.
- **GET** `/v1/users/search` - Search for a user by name.
- **POST** `/v1/users/{user-id}/relationship` - Modify the relationship between the current user and the target user.

## Actions

- list: List media (GET /v18.0/{userId}/media)
- get_by_id: Get media details (GET /v18.0/{mediaId})
- create: Create media container (POST /v18.0/{userId}/media)
- create_media_publish: Publish media (POST /v18.0/{userId}/media_publish)
- list_comments: List comments (GET /v18.0/{mediaId}/comments)
- create_comments: Reply to comment (POST /v18.0/{mediaId}/comments)
- list_insights: Get account insights (GET /v18.0/{userId}/insights)
- list_insights_2: Get media insights (GET /v18.0/{mediaId}/insights)
- list_stories: List stories (GET /v18.0/{userId}/stories)
- list_me: Get current user (GET /v18.0/me)
- search: Search for media in a given area. (GET /v1/media/search)
- delete: Remove a comment. (DELETE /v1/media/{media-id}/comments/{comment-id})
- create_comments_2: Create a comment on a media object. (POST /v1/media/{media-id}/comments)
- search_users: Search for a user by name. (GET /v1/users/search)
- create_relationship: Modify the relationship between the current user and the target user. (POST /v1/users/{user-id}/relationship)

## Fields

- `image_url`: string [REQUIRED for create photo]
- `caption`: string [OPTIONAL]
- `media_type`: string [REQUIRED] ("IMAGE", "VIDEO", "CAROUSEL_ALBUM")
- `creation_id`: string [REQUIRED for publish]
- `metric`: string [REQUIRED for insights]
- `period`: string [OPTIONAL] ("day", "week", "days_28", "lifetime")

## Example Request Bodies

**Create Media Container:**
```json
{"image_url": "https://example.com/photo.jpg", "caption": "Beautiful sunset #photography", "media_type": "IMAGE"}
```

**Publish Media:**
```json
{"creation_id": "17889234567890"}
```
