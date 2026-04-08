---
name: calcom-scheduling
description: Manage Cal.com event types, bookings, and availability. Use when the
  user mentions cal.com, calcom, booking, schedule, event type, availability.
version: 1.0.0
skill_type: external
base_url_env: CALCOM_BASE_URL
auth_env_var: CALCOM_API_KEY
auth_type: header
triggers:
  - cal.com
  - calcom
  - booking
  - schedule
  - event type
  - availability
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires CALCOM_BASE_URL and CALCOM_API_KEY environment variables.
---

# Calcom-Scheduling

Manage Cal.com event types, bookings, and availability. Use when the user mentions cal.com, calcom, booking, schedule, event type, availability.

## API Endpoints

- **GET** `/v1/event-types` - List event types
- **GET** `/v1/event-types/{eventTypeId}` - Get an event type
- **POST** `/v1/event-types` - Create an event type
- **PATCH** `/v1/event-types/{eventTypeId}` - Update an event type
- **DELETE** `/v1/event-types/{eventTypeId}` - Delete an event type
- **GET** `/v1/bookings` - List bookings
- **POST** `/v1/bookings` - Create a booking
- **DELETE** `/v1/bookings/{bookingId}/cancel` - Cancel a booking
- **GET** `/v1/schedules` - List schedules
- **GET** `/v1/availability` - Get availability

## Actions

- list: List event types (GET /v1/event-types)
- get_by_id: Get an event type (GET /v1/event-types/{eventTypeId})
- create: Create an event type (POST /v1/event-types)
- update: Update an event type (PATCH /v1/event-types/{eventTypeId})
- delete: Delete an event type (DELETE /v1/event-types/{eventTypeId})
- list_bookings: List bookings (GET /v1/bookings)
- create_bookings: Create a booking (POST /v1/bookings)
- delete_cancel: Cancel a booking (DELETE /v1/bookings/{bookingId}/cancel)
- list_schedules: List schedules (GET /v1/schedules)
- list_availability: Get availability (GET /v1/availability)

## Fields

- `title`: string [REQUIRED for create event type]
- `slug`: string [REQUIRED for create event type]
- `length`: integer [REQUIRED] (minutes)
- `eventTypeId`: integer [REQUIRED for booking]
- `start`: string [REQUIRED for booking] (ISO datetime)
- `name`: string [REQUIRED for booking] (attendee name)
- `email`: string [REQUIRED for booking] (attendee email)

## Example Request Bodies

**Create Event Type:**
```json
{"title": "30 Minute Meeting", "slug": "30-min-meeting", "length": 30}
```

**Create Booking:**
```json
{"eventTypeId": 12345, "start": "2025-06-15T10:00:00Z", "name": "John Doe", "email": "john@example.com"}
