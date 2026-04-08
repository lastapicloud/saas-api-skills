---
name: mux-video
description: Manage video assets and live streams via Mux. Use when the user mentions
  mux, video, stream, live stream, asset, playback.
version: 1.0.0
skill_type: external
base_url_env: MUX_BASE_URL
auth_env_var: MUX_TOKEN_SECRET
auth_user_env: MUX_TOKEN_ID
auth_type: basic
triggers:
  - mux
  - video
  - stream
  - live stream
  - asset
  - playback
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MUX_BASE_URL and MUX_TOKEN_SECRET environment variables.
---

# Mux-Video

Manage video assets and live streams via Mux. Use when the user mentions mux, video, stream, live stream, asset, playback.

## API Endpoints

- **GET** `/video/v1/assets` - List assets
- **POST** `/video/v1/assets` - Create asset
- **GET** `/video/v1/assets/{ASSET_ID}` - Get asset
- **DELETE** `/video/v1/assets/{ASSET_ID}` - Delete asset
- **GET** `/video/v1/live-streams` - List live streams
- **POST** `/video/v1/live-streams` - Create live stream
- **DELETE** `/video/v1/live-streams/{LIVE_STREAM_ID}` - Delete live stream
- **GET** `/video/v1/playback-ids/{PLAYBACK_ID}` - Get playback ID
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Fabric.Admin/fabricLocations/{location}/slbMuxInstances` - Returns a list of all software load balancer instances at a location.
- **GET** `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Fabric.Admin/fabricLocations/{location}/slbMuxInstances/{slbMuxInstance}` - Returns the requested software load balancer multiplexer instance.

## Actions

- list: List assets (GET /video/v1/assets)
- create: Create asset (POST /video/v1/assets)
- get_by_id: Get asset (GET /video/v1/assets/{ASSET_ID})
- delete: Delete asset (DELETE /video/v1/assets/{ASSET_ID})
- list_live_streams: List live streams (GET /video/v1/live-streams)
- create_live_streams: Create live stream (POST /video/v1/live-streams)
- delete_live_streams: Delete live stream (DELETE /video/v1/live-streams/{LIVE_STREAM_ID})
- get_by_id_playback_ids: Get playback ID (GET /video/v1/playback-ids/{PLAYBACK_ID})
- list_slbmuxinstances: Returns a list of all software load balancer instances at a location. (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Fabric.Admin/fabricLocations/{location}/slbMuxInstances)
- get_by_id_slbmuxinstances: Returns the requested software load balancer multiplexer instance. (GET /subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Fabric.Admin/fabricLocations/{location}/slbMuxInstances/{slbMuxInstance})

## Fields

- `input`: array [REQUIRED for create] (input URLs)
- `playback_policy`: array [OPTIONAL]
- `reduced_latency`: boolean [OPTIONAL]

## Example Request Bodies

**Create Asset:**
```json
{"input": [{"url": "https://storage.example.com/video.mp4"}], "playback_policy": ["public"]}
```

**Create Live Stream:**
```json
{"playback_policy": ["public"], "reduced_latency": true}
```
