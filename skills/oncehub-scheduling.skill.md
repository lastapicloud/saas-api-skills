---
name: oncehub-scheduling
description: Booking and scheduling via OnceHub. Use when the user mentions oncehub, scheduleonce, booking, appointment scheduling, event types.
version: 1.0.0
skill_type: external
base_url_env: ONCEHUB_BASE_URL
auth_env_var: ONCEHUB_API_KEY
auth_type: bearer
triggers:
  - oncehub
  - scheduleonce
  - booking
  - appointment scheduling
  - event types
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://developers.oncehub.com/
---

# Oncehub-Scheduling

Booking and scheduling via OnceHub. Use when the user mentions oncehub, scheduleonce, booking, appointment scheduling, event types.

## API Endpoints

- **GET** `/v2/booking-calendars` - List booking calendars
- **GET** `/v2/booking-calendars/{calendarId}` - Get booking calendar
- **GET** `/v2/bookings` - List bookings
- **POST** `/v2/bookings` - Create booking
- **GET** `/v2/bookings/{bookingId}` - Get booking
- **PATCH** `/v2/bookings/{bookingId}` - Update booking
- **DELETE** `/v2/bookings/{bookingId}` - Cancel booking
- **GET** `/v2/booking-pages` - List booking pages
- **GET** `/v2/booking-pages/{pageId}` - Get booking page
- **GET** `/v2/event-types` - List event types
- **GET** `/v2/event-types/{eventTypeId}` - Get event type
- **POST** `/v2/event-types` - Create event type
- **PATCH** `/v2/event-types/{eventTypeId}` - Update event type
- **DELETE** `/v2/event-types/{eventTypeId}` - Delete event type
- **GET** `/v2/scheduling-links` - List scheduling links
- **POST** `/v2/scheduling-links` - Create scheduling link
- **GET** `/v2/notifications/sms` - List SMS notifications
- **GET** `/v2/notifications/email` - List email notifications

## Actions

- list_calendars: List booking calendars (GET /v2/booking-calendars)
- get_calendar: Get booking calendar (GET /v2/booking-calendars/{calendarId})
- list_bookings: List bookings (GET /v2/bookings)
- create_booking: Create booking (POST /v2/bookings)
- get_booking: Get booking (GET /v2/bookings/{bookingId})
- update_booking: Update booking (PATCH /v2/bookings/{bookingId})
- cancel_booking: Cancel booking (DELETE /v2/bookings/{bookingId})
- list_booking_pages: List booking pages (GET /v2/booking-pages)
- get_booking_page: Get booking page (GET /v2/booking-pages/{pageId})
- list_event_types: List event types (GET /v2/event-types)
- get_event_type: Get event type (GET /v2/event-types/{eventTypeId})
- create_event_type: Create event type (POST /v2/event-types)
- update_event_type: Update event type (PATCH /v2/event-types/{eventTypeId})
- delete_event_type: Delete event type (DELETE /v2/event-types/{eventTypeId})
- list_scheduling_links: List scheduling links (GET /v2/scheduling-links)
- create_scheduling_link: Create scheduling link (POST /v2/scheduling-links)
- list_sms_notifications: List SMS notifications (GET /v2/notifications/sms)
- list_email_notifications: List email notifications (GET /v2/notifications/email)

## Fields

- `calendar_id`: string [REQUIRED for calendar] - Calendar ID
- `booking_id`: string [REQUIRED for booking] - Booking ID
- `start_time`: string [REQUIRED for create] - Start time (ISO 8601)
- `end_time`: string [REQUIRED for create] - End time (ISO 8601)
- `invitee_email`: string [REQUIRED for create] - Invitee email
- `invitee_name`: string [REQUIRED for create] - Invitee name
- `event_type_id`: string [REQUIRED for create] - Event type ID

## Example Request Bodies

**Create Booking:**
```json
{"calendar_id": "CALENDAR_ID", "start_time": "2024-01-15T10:00:00Z", "end_time": "2024-01-15T11:00:00Z", "invitee_email": "user@example.com", "invitee_name": "John Doe"}
```

**Create Event Type:**
```json
{"name": "30 Minute Meeting", "duration": 30, "timezone": "UTC"}
```
