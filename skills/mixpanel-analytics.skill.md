---
name: mixpanel-analytics
description: Track events, query analytics data, and manage user profiles in Mixpanel.
  Use when the user mentions mixpanel, analytics, event, funnel, retention, user profile,
  track.
version: 1.0.0
skill_type: external
base_url_env: MIXPANEL_BASE_URL
auth_env_var: MIXPANEL_SERVICE_ACCOUNT_SECRET
auth_type: basic
triggers:
  - mixpanel
  - analytics
  - event
  - funnel
  - retention
  - user profile
  - track
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires MIXPANEL_BASE_URL and MIXPANEL_SERVICE_ACCOUNT_SECRET environment
  variables.
---

# Mixpanel-Analytics

Track events, query analytics data, and manage user profiles in Mixpanel. Use when the user mentions mixpanel, analytics, event, funnel, retention, user profile, track.

## API Endpoints

- **POST** `/import` - Import events (ingestion API)
- **GET** `/api/2.0/events` - Query events
- **GET** `/api/2.0/events/top` - Get top events
- **GET** `/api/2.0/funnels` - Query funnels
- **GET** `/api/2.0/retention` - Query retention
- **POST** `/api/2.0/engage` - Query user profiles
- **POST** `/engage#profile-set` - Set user profile properties (ingestion API)

## Actions

- create: Import events (ingestion API) (POST /import)
- list: Query events (GET /api/2.0/events)
- list_top: Get top events (GET /api/2.0/events/top)
- list_funnels: Query funnels (GET /api/2.0/funnels)
- list_retention: Query retention (GET /api/2.0/retention)
- create_engage: Query user profiles (POST /api/2.0/engage)
- create_engageprofile_set: Set user profile properties (ingestion API) (POST /engage#profile-set)

## Fields

- `event`: string [REQUIRED for import_events] (event name)
- `properties`: object [REQUIRED for import_events] (event properties including distinct_id and time)
- `from_date`: string [REQUIRED for query_events, query_retention] (start date YYYY-MM-DD)
- `to_date`: string [REQUIRED for query_events, query_retention] (end date YYYY-MM-DD)
- `event_name`: string [OPTIONAL for query_events] (filter by event name)
- `funnel_id`: integer [REQUIRED for query_funnels] (funnel ID)
- `distinct_id`: string [REQUIRED for set_profile] (user distinct ID)
- `$set`: object [REQUIRED for set_profile] (profile properties to set)

## Example Request Bodies

**Import Events:**
```json
[{"event": "Sign Up", "properties": {"distinct_id": "user_123", "time": 1679000000, "$insert_id": "abc123"}}]
```

**Query Profiles:**
```json
{"filter_by_cohort": {"id": 1234}, "page": 0}
```

**Set Profile:**
```json
{"$token": "your_project_token", "$distinct_id": "user_123", "$set": {"$name": "Jane Doe", "plan": "premium"}}
```
