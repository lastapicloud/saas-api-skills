---
name: youtube-data
description: Manage YouTube videos, playlists, and channels. Use when the user mentions
  youtube, video, playlist, channel, subscriber.
version: 1.0.0
skill_type: external
base_url_env: YOUTUBE_BASE_URL
auth_env_var: GOOGLE_API_TOKEN
auth_type: bearer
triggers:
  - youtube
  - video
  - playlist
  - channel
  - subscriber
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires YOUTUBE_BASE_URL and GOOGLE_API_TOKEN environment variables.
---

# Youtube-Data

Manage YouTube videos, playlists, and channels. Use when the user mentions youtube, video, playlist, channel, subscriber.

## API Endpoints

- **GET** `/youtube/v3/videos` - List videos
- **GET** `/youtube/v3/search` - Search videos
- **POST** `/youtube/v3/videos` - Upload a video
- **PUT** `/youtube/v3/videos` - Update a video
- **DELETE** `/youtube/v3/videos` - Delete a video
- **GET** `/youtube/v3/playlists` - List playlists
- **POST** `/youtube/v3/playlists` - Create a playlist
- **GET** `/youtube/v3/playlistItems` - List playlist items
- **POST** `/youtube/v3/playlistItems` - Add to playlist
- **GET** `/youtube/v3/channels` - List channels
- **GET** `/v1/jobs` - Lists jobs.
- **GET** `/v1/reportTypes` - Lists report types.
- **POST** `/v1/jobs` - Creates a job and returns it.
- **GET** `/v1/jobs/{jobId}` - Gets a job.
- **GET** `/v1/media/{resourceName}` - Method for media download. Download is supported on the URI `/v1/media/{+name}?alt=media`.

## Actions

- list: List videos (GET /youtube/v3/videos)
- search: Search videos (GET /youtube/v3/search)
- create: Upload a video (POST /youtube/v3/videos)
- put_videos: Update a video (PUT /youtube/v3/videos)
- delete_videos: Delete a video (DELETE /youtube/v3/videos)
- list_playlists: List playlists (GET /youtube/v3/playlists)
- create_playlists: Create a playlist (POST /youtube/v3/playlists)
- list_playlistitems: List playlist items (GET /youtube/v3/playlistItems)
- create_playlistitems: Add to playlist (POST /youtube/v3/playlistItems)
- list_channels: List channels (GET /youtube/v3/channels)
- list_jobs: Lists jobs. (GET /v1/jobs)
- list_reporttypes: Lists report types. (GET /v1/reportTypes)
- create_jobs: Creates a job and returns it. (POST /v1/jobs)
- get_by_id: Gets a job. (GET /v1/jobs/{jobId})
- get_by_id_media: Method for media download. Download is supported on the URI `/v1/media/{+name}?a (GET /v1/media/{resourceName})

## Fields

- `snippet`: object [REQUIRED for create/update] with `title`, `description`, `categoryId`
- `status`: object [OPTIONAL] with `privacyStatus` ("public", "private", "unlisted")
- `part`: string [REQUIRED for queries] ("snippet,statistics,contentDetails")
- `q`: string [REQUIRED for search]
- `maxResults`: integer [OPTIONAL]

## Example Request Bodies

**Create Playlist:**
```json
{"snippet": {"title": "Tutorial Series", "description": "Step-by-step coding tutorials"}, "status": {"privacyStatus": "public"}}
```

**Add to Playlist:**
```json
{"snippet": {"playlistId": "PLxxxxxx", "resourceId": {"kind": "youtube#video", "videoId": "dQw4w9WgXcQ"}}}
```
