---
name: hive-tasks
description: Manage projects and actions via Hive. Use when the user mentions hive,
  task, project, action, workspace.
version: 1.0.0
skill_type: external
base_url_env: HIVE_BASE_URL
auth_env_var: HIVE_API_TOKEN
auth_type: bearer
triggers:
  - hive
  - task
  - project
  - action
  - workspace
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires HIVE_BASE_URL and HIVE_API_TOKEN environment variables.
---

# Hive-Tasks

Manage projects and actions via Hive. Use when the user mentions hive, task, project, action, workspace.

## API Endpoints

- **GET** `/api/v1/workspaces` - List workspaces
- **GET** `/api/v1/projects` - List projects
- **POST** `/api/v1/actions` - Create action
- **GET** `/api/v1/actions/{actionId}` - Get action
- **PUT** `/api/v1/actions/{actionId}` - Update action
- **DELETE** `/api/v1/actions/{actionId}` - Delete action
- **GET** `/api/v1/actions` - List actions
- **GET** `/api/v1/users` - List users
- **POST** `/getClip` - <p>Downloads an MP4 file (clip) containing the archived, on-demand media from the specified video stream over the
- **POST** `/getDASHStreamingSessionURL` - <p>Retrieves an MPEG Dynamic Adaptive Streaming over HTTP (DASH) URL for the stream. You can then open the URL in a
- **POST** `/getHLSStreamingSessionURL` - <p>Retrieves an HTTP Live Streaming (HLS) URL for the stream. You can then open the URL in a browser or media player to
- **POST** `/getImages` - Retrieves a list of Images corresponding to each timestamp for a given time range, sampling interval, and image format
- **POST** `/getMediaForFragmentList` - <p>Gets media for a list of fragments (specified by fragment number) from the archived data in an Amazon Kinesis video
- **POST** `/listFragments` - <p>Returns a list of <a>Fragment</a> objects from the specified stream and timestamp range within the archived
- **GET** `/{year}/{month}.json` - Archive API

## Actions

- list: List workspaces (GET /api/v1/workspaces)
- list_projects: List projects (GET /api/v1/projects)
- create: Create action (POST /api/v1/actions)
- get_by_id: Get action (GET /api/v1/actions/{actionId})
- update: Update action (PUT /api/v1/actions/{actionId})
- delete: Delete action (DELETE /api/v1/actions/{actionId})
- list_actions: List actions (GET /api/v1/actions)
- list_users: List users (GET /api/v1/users)
- create_getclip: <p>Downloads an MP4 file (clip) containing the archived, on-demand media from th (POST /getClip)
- create_getdashstreamingsessionurl: <p>Retrieves an MPEG Dynamic Adaptive Streaming over HTTP (DASH) URL for the str (POST /getDASHStreamingSessionURL)
- create_gethlsstreamingsessionurl: <p>Retrieves an HTTP Live Streaming (HLS) URL for the stream. You can then open (POST /getHLSStreamingSessionURL)
- create_getimages: Retrieves a list of Images corresponding to each timestamp for a given time rang (POST /getImages)
- create_getmediaforfragmentlist: <p>Gets media for a list of fragments (specified by fragment number) from the ar (POST /getMediaForFragmentList)
- create_listfragments: <p>Returns a list of <a>Fragment</a> objects from the specified stream and times (POST /listFragments)
- list_resource: Archive API (GET /{year}/{month}.json)

## Fields

- `title`: string [REQUIRED for create]
- `projectId`: string [REQUIRED for create]
- `assignees`: array [OPTIONAL]

## Example Request Bodies

**Create Action:**
```json
{"title": "Design homepage mockup", "projectId": "proj-abc123", "assignees": ["user-xyz789"]}
```

**Update Action:**
```json
{"title": "Design homepage mockup - Final", "status": "completed"}
```
