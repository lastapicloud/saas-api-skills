---
name: buffer-social
description: Schedule and manage Buffer social media posts. Use when the user mentions
  buffer, social media, schedule, post, publish.
version: 1.0.0
skill_type: external
base_url_env: BUFFER_BASE_URL
auth_env_var: BUFFER_ACCESS_TOKEN
auth_type: bearer
triggers:
  - buffer
  - social media
  - schedule
  - post
  - publish
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires BUFFER_BASE_URL and BUFFER_ACCESS_TOKEN environment variables.
---

# Buffer-Social

Schedule and manage Buffer social media posts. Use when the user mentions buffer, social media, schedule, post, publish.

## API Endpoints

- **GET** `/1/profiles.json` - List profiles
- **GET** `/1/profiles/{profileId}.json` - Get a profile
- **GET** `/1/profiles/{profileId}/updates/pending.json` - List pending updates
- **GET** `/1/profiles/{profileId}/updates/sent.json` - List sent updates
- **POST** `/1/updates/create.json` - Create an update
- **POST** `/1/updates/{updateId}/update.json` - Update an update
- **POST** `/1/updates/{updateId}/destroy.json` - Delete an update
- **POST** `/1/updates/{updateId}/share.json` - Share now
- **GET** `/1/user.json` - Get current user
- **GET** `/1/info/configuration{mediaTypeExtension}` - Returns an object with the current configuration that Buffer is using, including supported services, their icons and
- **POST** `/1/updates/create{mediaTypeExtension}` - Create one or more new status updates.
- **GET** `/1/links/shares{mediaTypeExtension}` - Returns an object with a the numbers of shares a link has had using Buffer.
- **GET** `/1/profiles/{id}{mediaTypeExtension}` - Returns details of the single specified social media profile.
- **GET** `/1/profiles{mediaTypeExtension}` - Returns an array of social media profiles connected to a users account.
- **GET** `/1/updates/{id}{mediaTypeExtension}` - Returns a single social media update.

## Actions

- list: List profiles (GET /1/profiles.json)
- list_profiles: Get a profile (GET /1/profiles/{profileId}.json)
- list_pending_json: List pending updates (GET /1/profiles/{profileId}/updates/pending.json)
- list_sent_json: List sent updates (GET /1/profiles/{profileId}/updates/sent.json)
- create: Create an update (POST /1/updates/create.json)
- create_update_json: Update an update (POST /1/updates/{updateId}/update.json)
- create_destroy_json: Delete an update (POST /1/updates/{updateId}/destroy.json)
- create_share_json: Share now (POST /1/updates/{updateId}/share.json)
- list_user_json: Get current user (GET /1/user.json)
- list_configurationmediatypeextension: Returns an object with the current configuration that Buffer is using, including (GET /1/info/configuration{mediaTypeExtension})
- create_createmediatypeextension: Create one or more new status updates. (POST /1/updates/create{mediaTypeExtension})
- list_sharesmediatypeextension: Returns an object with a the numbers of shares a link has had using Buffer. (GET /1/links/shares{mediaTypeExtension})
- get_by_id: Returns details of the single specified social media profile. (GET /1/profiles/{id}{mediaTypeExtension})
- list_profilesmediatypeextension: Returns an array of social media profiles connected to a users account. (GET /1/profiles{mediaTypeExtension})
- get_by_id_updates: Returns a single social media update. (GET /1/updates/{id}{mediaTypeExtension})

## Fields

- `text`: string [REQUIRED for create]
- `profile_ids`: array [REQUIRED for create]
- `scheduled_at`: string [OPTIONAL] (ISO datetime)
- `media`: object [OPTIONAL] with `link`, `description`, `picture`

## Example Request Bodies

**Create Update:**
```json
{"text": "Excited to announce our new product launch!", "profile_ids": ["prof_abc123"], "scheduled_at": "2026-04-20T14:00:00Z"}
```

**Update an Update:**
```json
{"text": "Updated: Our product launch is live now!", "scheduled_at": "2026-04-20T16:00:00Z"}
```
