---
name: twitter-social
description: Manage Twitter/X posts, users, and timelines. Use when the user mentions
  twitter, X, tweet, post, timeline, social.
version: 1.0.0
skill_type: external
base_url_env: TWITTER_BASE_URL
auth_env_var: TWITTER_BEARER_TOKEN
auth_type: bearer
triggers:
  - twitter
  - X
  - tweet
  - post
  - timeline
  - social
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires TWITTER_BASE_URL and TWITTER_BEARER_TOKEN environment variables.
---

# Twitter-Social

Manage Twitter/X posts, users, and timelines. Use when the user mentions twitter, X, tweet, post, timeline, social.

## API Endpoints

- **POST** `/2/tweets` - Create a tweet
- **GET** `/2/tweets/{tweetId}` - Get a tweet
- **DELETE** `/2/tweets/{tweetId}` - Delete a tweet
- **GET** `/2/users/me` - Get current user
- **GET** `/2/users/{userId}/tweets` - Get user tweets
- **GET** `/2/users/by/username/{username}` - Lookup user by username
- **GET** `/2/tweets/search/recent` - Search recent tweets
- **POST** `/2/users/{userId}/likes` - Like a tweet
- **POST** `/2/users/{userId}/retweets` - Retweet
- **GET** `/2/users/{userId}/followers` - Get followers
- **GET** `/2/spaces/search` - Search for Spaces
- **POST** `/2/compliance/jobs` - Create compliance job
- **PUT** `/2/lists/{id}` - Update List.
- **DELETE** `/2/lists/{id}` - Delete List
- **GET** `/2/compliance/jobs` - List Compliance Jobs

## Actions

- create: Create a tweet (POST /2/tweets)
- get_by_id: Get a tweet (GET /2/tweets/{tweetId})
- delete: Delete a tweet (DELETE /2/tweets/{tweetId})
- list: Get current user (GET /2/users/me)
- list_tweets: Get user tweets (GET /2/users/{userId}/tweets)
- get_by_id_username: Lookup user by username (GET /2/users/by/username/{username})
- list_recent: Search recent tweets (GET /2/tweets/search/recent)
- create_likes: Like a tweet (POST /2/users/{userId}/likes)
- create_retweets: Retweet (POST /2/users/{userId}/retweets)
- list_followers: Get followers (GET /2/users/{userId}/followers)
- search: Search for Spaces (GET /2/spaces/search)
- create_jobs: Create compliance job (POST /2/compliance/jobs)
- update: Update List. (PUT /2/lists/{id})
- delete_lists: Delete List (DELETE /2/lists/{id})
- list_jobs: List Compliance Jobs (GET /2/compliance/jobs)

## Fields

- `text`: string [REQUIRED for create]
- `reply`: object [OPTIONAL] with `in_reply_to_tweet_id`
- `media`: object [OPTIONAL] with `media_ids`
- `query`: string [REQUIRED for search]
- `tweet_id`: string [REQUIRED for like/retweet]
- `max_results`: integer [OPTIONAL]

## Example Request Bodies

**Create Tweet:**
```json
{"text": "Excited to announce our new API integration!"}
```

**Like a Tweet:**
```json
{"tweet_id": "1234567890123456789"}
