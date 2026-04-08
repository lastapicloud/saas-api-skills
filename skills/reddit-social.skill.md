---
name: reddit-social
description: Manage Reddit posts, comments, and subreddits. Use when the user mentions
  reddit, post, comment, subreddit, social.
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
- **GET** `/me/karma` - Get user karma

## Actions

- list: Get current user (GET /api/v1/me)
- list_hot: List hot posts (GET /r/{subreddit}/hot)
- list_new: List new posts (GET /r/{subreddit}/new)
- list_top: List top posts (GET /r/{subreddit}/top)
- list_rising: List rising posts (GET /r/{subreddit}/rising)
- create: Create a post (POST /api/submit)
- create_comment: Add a comment (POST /api/comment)
- create_vote: Vote on a post/comment (POST /api/vote)
- delete: Delete a post or comment (DELETE /api/delete)
- list_about: Get subreddit info (GET /r/{subreddit}/about)
- search: Search in subreddit (GET /r/{subreddit}/search)
- list_about_2: Get user info (GET /user/{username}/about)
- list_posts: Get user posts (GET /user/{username}/posts)
- list_comments: Get user comments (GET /user/{username}/comments)
- list_subscriber: List subscribed subreddits (GET /subreddits/mine/subscriber)
- list_karma: Get user karma (GET /me/karma)

## Fields

- `sr`: string [REQUIRED for create post] (subreddit name)
- `title`: string [REQUIRED for create post]
- `kind`: string [REQUIRED] ("self", "link", "image")
- `text`: string [OPTIONAL for self posts]
- `url`: string [OPTIONAL for link posts]
- `parent`: string [REQUIRED for comment] (thing ID)
- `dir`: integer [REQUIRED for vote] (1, 0, or -1)

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
