---
name: logrocket-monitoring
description: Session replay and debugging via LogRocket. Use when the user mentions logrocket, session replay, debugging, user recording, frontend monitoring.
version: 1.0.0
skill_type: external
base_url_env: LOGROCKET_BASE_URL
auth_env_var: LOGROCKET_APP_ID
auth_type: basic
triggers:
  - logrocket
  - session replay
  - debugging
  - user recording
  - frontend monitoring
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://docs.logrocket.com/
---

# Logrocket-Monitoring

Session replay and debugging via LogRocket. Use when the user mentions logrocket, session replay, debugging, user recording, frontend monitoring.

## API Endpoints

- **POST** `/sessions` - Create session
- **GET** `/sessions/{sessionId}` - Get session
- **GET** `/sessions` - List sessions
- **GET** `/sessions/{sessionId}/events` - Get session events
- **GET** `/sessions/{sessionId}/errors` - Get session errors
- **POST** `/events` - Record event
- **GET** `/errors` - List errors
- **GET** `/errors/{errorId}` - Get error details

## Actions

- create_session: Create session (POST /sessions)
- get_session: Get session (GET /sessions/{sessionId})
- list_sessions: List sessions (GET /sessions)
- get_events: Get session events (GET /sessions/{sessionId}/events)
- get_errors: Get session errors (GET /sessions/{sessionId}/errors)
- record_event: Record event (POST /events)
- list_errors: List errors (GET /errors)
- get_error: Get error details (GET /errors/{errorId})

## Fields

- `appId`: string [REQUIRED] - Application ID
- `userId`: string [OPTIONAL] - User ID
- `sessionId`: string [REQUIRED] - Session ID
- `event`: string [REQUIRED for event] - Event name
- `properties`: object [OPTIONAL] - Event properties
- `message`: string [REQUIRED for error] - Error message

## Example Request Bodies

**Create Session:**
```json
{"appId": "APP_ID", "userId": "user123"}
```

**Record Event:**
```json
{"sessionId": "SESSION_ID", "event": "button_click", "properties": {"button": "submit"}}
```
