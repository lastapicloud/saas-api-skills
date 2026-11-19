---
name: youcanbookme-scheduling
description: Online scheduling via YouCanBookMe. Use when the user mentions youcanbookme, ycbm, booking, appointment, scheduling.
version: 1.0.0
skill_type: external
base_url_env: YOUCANBOOKME_BASE_URL
auth_env_var: YOUCANBOOKME_API_KEY
auth_type: bearer
triggers:
  - youcanbookme
  - ycbm
  - booking
  - appointment scheduling
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://ycbm.stoplight.io/
---

# Youcanbookme-Scheduling

Online scheduling via YouCanBookMe. Use when the user mentions youcanbookme, ycbm, booking, appointment, scheduling.

## API Endpoints

- **GET** `/bookings` - Query bookings
- **POST** `/bookings` - Create booking
- **GET** `/bookings/{bookingId}` - Get booking
- **PATCH** `/bookings/{bookingId}` - Update booking
- **DELETE** `/bookings/{bookingId}` - Cancel booking
- **GET** `/calendars` - List calendars
- **GET** `/calendars/{calendarId}` - Get calendar
- **GET** `/event-types` - List event types
- **GET** `/event-types/{eventTypeId}` - Get event type
- **GET** `/settings` - Get account settings
- **GET** `/settings/{settingKey}` - Get specific setting

## Actions

- list_bookings: Query bookings (GET /bookings)
- create_booking: Create booking (POST /bookings)
- get_booking: Get booking (GET /bookings/{bookingId})
- update_booking: Update booking (PATCH /bookings/{bookingId})
- cancel_booking: Cancel booking (DELETE /bookings/{bookingId})
- list_calendars: List calendars (GET /calendars)
- get_calendar: Get calendar (GET /calendars/{calendarId})
- list_event_types: List event types (GET /event-types)
- get_event_type: Get event type (GET /event-types/{eventTypeId})
- get_settings: Get account settings (GET /settings)
- get_setting: Get specific setting (GET /settings/{settingKey})

## Fields

- `calendar_id`: string [REQUIRED] - Calendar ID
- `booking_id`: string [REQUIRED for get/update/cancel] - Booking ID
- `event_type`: string [REQUIRED for create] - Event type ID
- `name`: string [REQUIRED for create] - Booker's name
- `email`: string [REQUIRED for create] - Booker's email
- `start_date_time`: string [REQUIRED for create] - Start date/time (ISO 8601)
- `notes`: string [OPTIONAL] - Booking notes

## Example Request Bodies

**Create Booking:**
```json
{"calendar_id": "CALENDAR_ID", "event_type": "30min", "name": "John Doe", "email": "john@example.com", "start_date_time": "2024-01-15T10:00:00Z"}
```

**Update Booking:**
```json
{"notes": "Updated notes", "start_date_time": "2024-01-15T11:00:00Z"}
```
