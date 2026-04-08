---
name: calendly-scheduling
description: Manage event types, scheduled events, and invitees in Calendly. Use when
  the user mentions calendly, schedule, event, meeting, booking, availability, invitee.
version: 1.0.0
skill_type: external
base_url_env: CALENDLY_BASE_URL
auth_env_var: CALENDLY_ACCESS_TOKEN
auth_type: bearer
triggers:
  - calendly
  - schedule
  - event
  - meeting
  - booking
  - availability
  - invitee
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CALENDLY_BASE_URL and CALENDLY_ACCESS_TOKEN environment variables.
---

# Calendly-Scheduling

Manage event types, scheduled events, and invitees in Calendly. Use when the user mentions calendly, schedule, event, meeting, booking, availability, invitee.

## API Endpoints

- **GET** `/users/me` - Get current user
- **GET** `/event_types` - List event types
- **GET** `/event_types/{uuid}` - Get an event type
- **GET** `/scheduled_events` - List scheduled events
- **GET** `/scheduled_events/{uuid}` - Get a scheduled event
- **GET** `/scheduled_events/{uuid}/invitees` - List invitees for an event
- **POST** `/scheduling_links` - Create a scheduling link
- **GET** `/organization_memberships` - List organization members
- **POST** `/invitee_no_shows` - Create Invitee No Show
- **GET** `/invitee_no_shows/{uuid}` - Get Invitee No Show
- **DELETE** `/invitee_no_shows/{uuid}` - Delete Invitee No Show
- **GET** `/organizations/{uuid}/invitations` - List Organization Invitations
- **POST** `/organizations/{uuid}/invitations` - Invite User to Organization
- **GET** `/organizations/{org_uuid}/invitations/{uuid}` - Get Organization Invitation
- **DELETE** `/organizations/{org_uuid}/invitations/{uuid}` - Revoke User's Organization Invitation

## Actions

- list: Get current user (GET /users/me)
- list_event_types: List event types (GET /event_types)
- get_by_id: Get an event type (GET /event_types/{uuid})
- list_scheduled_events: List scheduled events (GET /scheduled_events)
- get_by_id_scheduled_events: Get a scheduled event (GET /scheduled_events/{uuid})
- list_invitees: List invitees for an event (GET /scheduled_events/{uuid}/invitees)
- create: Create a scheduling link (POST /scheduling_links)
- list_organization_memberships: List organization members (GET /organization_memberships)
- create_invitee_no_shows: Create Invitee No Show (POST /invitee_no_shows)
- get_by_id_invitee_no_shows: Get Invitee No Show (GET /invitee_no_shows/{uuid})
- delete: Delete Invitee No Show (DELETE /invitee_no_shows/{uuid})
- list_invitations: List Organization Invitations (GET /organizations/{uuid}/invitations)
- create_invitations: Invite User to Organization (POST /organizations/{uuid}/invitations)
- get_by_id_invitations: Get Organization Invitation (GET /organizations/{org_uuid}/invitations/{uuid})
- delete_invitations: Revoke User's Organization Invitation (DELETE /organizations/{org_uuid}/invitations/{uuid})

## Fields

- `uuid`: string [REQUIRED for get/list by ID actions] (resource UUID)
- `user`: string [REQUIRED for list_event_types, list_scheduled_events] (user URI)
- `organization`: string [REQUIRED for list_members, list_scheduled_events] (organization URI)
- `owner`: string [REQUIRED for create_scheduling_link] (event type URI)
- `max_event_count`: integer [OPTIONAL for create_scheduling_link] (max bookings, 1 for single-use)
- `status`: string [OPTIONAL for list_scheduled_events] (active or canceled)
- `min_start_time`: string [OPTIONAL] (ISO 8601 datetime filter)
- `max_start_time`: string [OPTIONAL] (ISO 8601 datetime filter)
- `count`: integer [OPTIONAL] (results per page)

## Example Request Bodies

**Create Scheduling Link:**
```json
{"max_event_count": 1, "owner": "https://api.calendly.com/event_types/abc123", "owner_type": "EventType"}
```

**List Scheduled Events (Query Params):**
Query parameter: `user=https://api.calendly.com/users/abc123&status=active&count=20`
