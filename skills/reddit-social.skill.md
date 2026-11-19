---
name: reddit-social
description: 'Manage Reddit posts, comments, and subreddits. Use when the user mentions
  reddit, post, comment, subreddit, social.

  '
version: 1.0.0
skill_type: external
base_url_env: REDDIT_BASE_URL
auth_env_var: REDDIT_ACCESS_TOKEN
auth_type: bearer
triggers:
  - reddit
  - post
  - comment
  - subreddit
  - social
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires REDDIT_BASE_URL and REDDIT_ACCESS_TOKEN environment variables.
annotations:
  readOnlyHint: false
  destructiveHint: true
  idempotentHint: false
---

# Reddit-Social

Manage Reddit posts, comments, and subreddits. Use when the user mentions reddit, post, comment, subreddit, social.


## API Endpoints

- **GET** `/api/v1/me` - Get current user
- **GET** `/r/{subreddit}/hot` - List hot posts
- **GET** `/r/{subreddit}/new` - List new posts
- **GET** `/r/{subreddit}/top` - List top posts
- **GET** `/r/{subreddit}/rising` - List rising posts
- **POST** `/api/submit` - Create a post
- **POST** `/api/comment` - Add a comment
- **POST** `/api/vote` - Vote on a post/comment
- **DELETE** `/api/delete` - Delete a post or comment
- **GET** `/r/{subreddit}/about` - Get subreddit info
- **GET** `/r/{subreddit}/search` - Search in subreddit
- **GET** `/user/{username}/about` - Get user info
- **GET** `/user/{username}/posts` - Get user posts
- **GET** `/user/{username}/comments` - Get user comments
- **GET** `/subreddits/mine/subscriber` - List subscribed subreddits

## Actions

- list: Get current user (GET /api/v1/me)
- list_hot_posts: List hot posts (GET /r/{subreddit}/hot)
- list_new_posts: List new posts (GET /r/{subreddit}/new)
- list_top_posts: List top posts (GET /r/{subreddit}/top)
- list_rising_posts: List rising posts (GET /r/{subreddit}/rising)
- create: Create a post (POST /api/submit)
- add_comment: Add a comment (POST /api/comment)
- create_vote_postcomment: Vote on a post/comment (POST /api/vote)
- delete: Delete a post or comment (DELETE /api/delete)
- get_subreddit_info: Get subreddit info (GET /r/{subreddit}/about)
- search: Search in subreddit (GET /r/{subreddit}/search)
- get_user_info: Get user info (GET /user/{username}/about)
- get_user_posts: Get user posts (GET /user/{username}/posts)
- get_user_comments: Get user comments (GET /user/{username}/comments)
- list_subscribed_subreddits: List subscribed subreddits (GET /subreddits/mine/subscriber)

## Fields

- `sr`: string [REQUIRED for create post] (subreddit name) — Sr
- `title`: string [REQUIRED for create post] — Title or heading
- `kind`: string [REQUIRED] ("self", "link", "image") — Kind
- `text`: string [OPTIONAL for self posts] — Text content
- `url`: string [OPTIONAL for link posts] — URL
- `parent`: string [REQUIRED for comment] (thing ID) — Parent
- `dir`: integer [REQUIRED for vote] (1, 0, or -1) — Dir value

## Example Request Bodies

**Create Post:**
```json
{"sr": "programming", "title": "Understanding REST API Design", "kind": "self", "text": "Here are some best practices for REST API design..."}
```

**Add Comment:**
```json
{"parent": "t3_abc123", "text": "Great post, thanks for sharing!"}
```

**Vote:**
```json
{"id": "t3_abc123", "dir": 1}
```

## Response

**About object:**
- `id`: string — Unique about identifier
- `name`: string — About name or title
- `status`: string — Current status
- `created_at`: string — Creation timestamp (ISO 8601)
- `updated_at`: string — Last update timestamp (ISO 8601)

## Error Responses

| Status | Meaning |
|--------|---------|
| 400 | Invalid request body — check required fields and types |
| 401 | Authentication failed — verify API key or token is valid and not expired |
| 403 | Forbidden — insufficient permissions or scope for this action |
| 404 | Resource not found — check the ID or identifier |
| 409 | Conflict — resource already exists or concurrent modification |
| 429 | Rate limited — too many requests, retry after delay |
| 500 | Server error — retry or check service status page |
