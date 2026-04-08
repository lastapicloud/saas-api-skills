---
name: api-video
description: Upload, manage, and stream videos via api.video. Use when the user mentions
  api.video, video, stream, upload, live stream, player.
version: 1.0.0
skill_type: external
base_url_env: API_VIDEO_BASE_URL
auth_env_var: API_VIDEO_API_KEY
auth_type: bearer
triggers:
  - api.video
  - video
  - stream
  - upload
  - live stream
  - player
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires API_VIDEO_BASE_URL and API_VIDEO_API_KEY environment variables.
---

# Api-Video

Upload, manage, and stream videos via api.video. Use when the user mentions api.video, video, stream, upload, live stream, player.

## API Endpoints

- **GET** `/videos` - List videos
- **POST** `/videos` - Create a video object
- **GET** `/videos/{videoId}` - Get video details
- **PATCH** `/videos/{videoId}` - Update video metadata
- **DELETE** `/videos/{videoId}` - Delete a video
- **POST** `/videos/{videoId}/source` - Upload a video file
- **GET** `/live-streams` - List live streams
- **POST** `/live-streams` - Create a live stream
- **GET** `/v1/{name}` - Gets details about a Network Connectivity Center spoke.
- **PATCH** `/v1/{name}` - Updates the parameters of a Network Connectivity Center spoke.
- **GET** `/v1/{name}/locations` - Lists information about the supported locations for this service.
- **GET** `/v1/{name}/operations` - Lists operations that match the specified filter in the request. If the server doesn't support this method, it returns
- **GET** `/v1/{parent}/hubs` - Lists the Network Connectivity Center hubs associated with a given project.
- **GET** `/v1/{parent}/spokes` - Lists the Network Connectivity Center spokes in a specified project and location.
- **GET** `/v1/{resource}:getIamPolicy` - Gets the access control policy for a resource. Returns an empty policy if the resource exists and does not have a

## Actions

- list: List videos (GET /videos)
- create: Create a video object (POST /videos)
- get_by_id: Get video details (GET /videos/{videoId})
- update: Update video metadata (PATCH /videos/{videoId})
- delete: Delete a video (DELETE /videos/{videoId})
- create_source: Upload a video file (POST /videos/{videoId}/source)
- list_live_streams: List live streams (GET /live-streams)
- create_live_streams: Create a live stream (POST /live-streams)
- get_by_id_v1: Gets details about a Network Connectivity Center spoke. (GET /v1/{name})
- update_v1: Updates the parameters of a Network Connectivity Center spoke. (PATCH /v1/{name})
- list_locations: Lists information about the supported locations for this service. (GET /v1/{name}/locations)
- list_operations: Lists operations that match the specified filter in the request. If the server d (GET /v1/{name}/operations)
- list_hubs: Lists the Network Connectivity Center hubs associated with a given project. (GET /v1/{parent}/hubs)
- list_spokes: Lists the Network Connectivity Center spokes in a specified project and location (GET /v1/{parent}/spokes)
- list_v1: Gets the access control policy for a resource. Returns an empty policy if the re (GET /v1/{resource}:getIamPolicy)

## Fields

- `title`: string [REQUIRED for create]
- `description`: string [OPTIONAL]
- `public`: boolean [OPTIONAL]

## Example Request Bodies

**Create Video:**
```json
{"title": "Product Demo", "description": "A walkthrough of the new features", "public": true}
```

**Update Video:**
```json
{"title": "Updated Product Demo", "description": "Revised walkthrough"}
