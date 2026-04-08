---
name: amplitude-analytics
description: Manage Amplitude events, user properties, and cohorts. Use when the user
  mentions amplitude, analytics, event, cohort, user property.
version: 1.0.0
skill_type: external
base_url_env: AMPLITUDE_BASE_URL
auth_env_var: AMPLITUDE_API_KEY
auth_type: header
triggers:
  - amplitude
  - analytics
  - event
  - cohort
  - user property
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires AMPLITUDE_BASE_URL and AMPLITUDE_API_KEY environment variables.
---

# Amplitude-Analytics

Manage Amplitude events, user properties, and cohorts. Use when the user mentions amplitude, analytics, event, cohort, user property.

## API Endpoints

- **POST** `/2/httpapi` - Track events
- **GET** `/2/usersearch` - Search users
- **GET** `/2/useractivity` - Get user activity
- **POST** `/2/identify` - Set user properties
- **GET** `/3/cohorts` - List cohorts
- **GET** `/3/chart/{chartId}/query` - Query a chart
- **GET** `/2/events/segmentation` - Event segmentation
- **GET** `/2/events/list` - List event types
- **GET** `/2/taxonomy/event` - Get event taxonomy
- **GET** `/2/export` - Export raw data

## Actions

- create: Track events (POST /2/httpapi)
- search: Search users (GET /2/usersearch)
- list: Get user activity (GET /2/useractivity)
- create_identify: Set user properties (POST /2/identify)
- list_cohorts: List cohorts (GET /3/cohorts)
- query: Query a chart (GET /3/chart/{chartId}/query)
- list_segmentation: Event segmentation (GET /2/events/segmentation)
- list_events: List event types (GET /2/events/list)
- list_event: Get event taxonomy (GET /2/taxonomy/event)
- list_export: Export raw data (GET /2/export)

## Fields

- `events`: array [REQUIRED for track] with `event_type`, `user_id`, `event_properties`
- `user`: string [REQUIRED for search]
- `e`: string [REQUIRED for segmentation] (event JSON)
- `start`: string [REQUIRED for segmentation] (YYYYMMDD)
- `end`: string [REQUIRED for segmentation] (YYYYMMDD)

## Example Request Bodies

**Track Events:**
```json
{"events": [{"event_type": "purchase", "user_id": "user_123", "event_properties": {"item": "T-Shirt", "price": 29.99}}]}
```

**Set User Properties:**
```json
{"identification": [{"user_id": "user_123", "user_properties": {"plan": "premium", "signup_date": "2025-01-15"}}]}
