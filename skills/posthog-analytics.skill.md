---
name: posthog-analytics
description: Track events, manage feature flags, cohorts, and experiments in PostHog.
  Use when the user mentions posthog, analytics, event, feature flag, cohort, insight,
  funnel, experiment.
version: 1.0.0
skill_type: external
base_url_env: POSTHOG_BASE_URL
auth_env_var: POSTHOG_API_KEY
auth_type: bearer
triggers:
  - posthog
  - analytics
  - event
  - feature flag
  - cohort
  - insight
  - funnel
  - experiment
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires POSTHOG_BASE_URL and POSTHOG_API_KEY environment variables.
---

# Posthog-Analytics

Track events, manage feature flags, cohorts, and experiments in PostHog. Use when the user mentions posthog, analytics, event, feature flag, cohort, insight, funnel, experiment.

## API Endpoints

- **POST** `/capture/` - Send an event
- **GET** `/api/projects/{project_id}/events/` - List events
- **GET** `/api/projects/{project_id}/persons/` - List persons/users
- **GET** `/api/projects/{project_id}/insights/` - Get analytics insights
- **GET** `/api/projects/{project_id}/feature_flags/` - List feature flags
- **POST** `/api/projects/{project_id}/feature_flags/` - Create a feature flag
- **GET** `/api/projects/{project_id}/cohorts/` - List cohorts
- **GET** `/api/projects/{project_id}/experiments/` - List experiments
- **GET** `/api/environments/:environment_id/eventscURLPostHog`
- **GET** `/api/environments/:environment_id/events`
- **GET** `/api/environments/:environment_id/events/:idcURLPostHog`
- **GET** `/api/environments/:environment_id/events/:id`
- **GET** `/api/environments/:environment_id/events/valuescURLPostHog`
- **GET** `/api/environments/:environment_id/events/values`
- **GET** `/api/projects/:project_id/eventscURLPostHog`

## Actions

- create: Send an event (POST /capture/)
- list: List events (GET /api/projects/{project_id}/events/)
- list_persons: List persons/users (GET /api/projects/{project_id}/persons/)
- list_insights: Get analytics insights (GET /api/projects/{project_id}/insights/)
- list_feature_flags: List feature flags (GET /api/projects/{project_id}/feature_flags/)
- create_feature_flags: Create a feature flag (POST /api/projects/{project_id}/feature_flags/)
- list_cohorts: List cohorts (GET /api/projects/{project_id}/cohorts/)
- list_experiments: List experiments (GET /api/projects/{project_id}/experiments/)
- list_eventscurlposthog: GET /api/environments/:environment_id/eventscURLPostHog (GET /api/environments/:environment_id/eventscURLPostHog)
- list_events: GET /api/environments/:environment_id/events (GET /api/environments/:environment_id/events)
- list_idcurlposthog: GET /api/environments/:environment_id/events/:idcURLPostHog (GET /api/environments/:environment_id/events/:idcURLPostHog)
- list_id: GET /api/environments/:environment_id/events/:id (GET /api/environments/:environment_id/events/:id)
- list_valuescurlposthog: GET /api/environments/:environment_id/events/valuescURLPostHog (GET /api/environments/:environment_id/events/valuescURLPostHog)
- list_values: GET /api/environments/:environment_id/events/values (GET /api/environments/:environment_id/events/values)
- list_eventscurlposthog_2: GET /api/projects/:project_id/eventscURLPostHog (GET /api/projects/:project_id/eventscURLPostHog)

## Fields

- `api_key`: string [REQUIRED for capture_event] (project API key, sent in the event body)
- `event`: string [REQUIRED for capture_event] (event name)
- `distinct_id`: string [REQUIRED for capture_event] (unique user identifier)
- `properties`: object [OPTIONAL for capture_event] (event properties)
- `name`: string [REQUIRED for create_feature_flag] (feature flag key)
- `key`: string [REQUIRED for create_feature_flag] (feature flag key, unique identifier)
- `filters`: object [OPTIONAL for create_feature_flag] (rollout conditions)
- `active`: boolean [OPTIONAL for create_feature_flag] (whether the flag is active)
- `limit`: integer [OPTIONAL] (number of results to return)

## Example Request Bodies

**Capture Event:**
```json
{
  "api_key": "phc_your_project_api_key",
  "event": "page_view",
  "distinct_id": "user-123",
  "properties": {
    "page": "/home",
    "$current_url": "https://example.com/home"
  }
}
```

**Create Feature Flag:**
```json
{
  "key": "new-dashboard",
  "name": "New Dashboard",
  "filters": {
    "groups": [
      {
        "rollout_percentage": 50
      }
    ]
  },
  "active": true
}
```
