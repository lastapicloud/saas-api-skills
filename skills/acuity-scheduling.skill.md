---
name: acuity-scheduling
description: Manage Acuity Scheduling appointments and calendars. Use when the user
  mentions acuity, appointment, scheduling, booking, calendar.
version: 1.0.0
skill_type: external
base_url_env: ACUITY_BASE_URL
auth_env_var: ACUITY_API_KEY
auth_user_env: ACUITY_USER_ID
auth_type: basic
triggers:
  - acuity
  - appointment
  - scheduling
  - booking
  - calendar
license: Apache-2.0
metadata:
  author: lastapi
  version: 1.0.0
compatibility: Requires ACUITY_BASE_URL and ACUITY_API_KEY environment variables.
---

# Acuity-Scheduling

Manage Acuity Scheduling appointments and calendars. Use when the user mentions acuity, appointment, scheduling, booking, calendar.

## API Endpoints

- **GET** `/api/v1/appointments` - List appointments
- **GET** `/api/v1/appointments/{appointmentId}` - Get an appointment
- **POST** `/api/v1/appointments` - Create an appointment
- **PUT** `/api/v1/appointments/{appointmentId}` - Update an appointment
- **PUT** `/api/v1/appointments/{appointmentId}/cancel` - Cancel an appointment
- **GET** `/api/v1/appointment-types` - List appointment types
- **GET** `/api/v1/calendars` - List calendars
- **GET** `/api/v1/availability/dates` - Get available dates
- **GET** `/api/v1/availability/times` - Get available times
- **GET** `/api/v1/me` - Get current user

## Actions

- list: List appointments (GET /api/v1/appointments)
- get_by_id: Get an appointment (GET /api/v1/appointments/{appointmentId})
- create: Create an appointment (POST /api/v1/appointments)
- update: Update an appointment (PUT /api/v1/appointments/{appointmentId})
- put_cancel: Cancel an appointment (PUT /api/v1/appointments/{appointmentId}/cancel)
- list_appointment_types: List appointment types (GET /api/v1/appointment-types)
- list_calendars: List calendars (GET /api/v1/calendars)
- list_dates: Get available dates (GET /api/v1/availability/dates)
- list_times: Get available times (GET /api/v1/availability/times)
- list_me: Get current user (GET /api/v1/me)

## Fields

- `datetime`: string [REQUIRED for create] (ISO datetime)
- `appointmentTypeID`: integer [REQUIRED for create]
- `firstName`: string [REQUIRED for create]
- `lastName`: string [REQUIRED for create]
- `email`: string [REQUIRED for create]
- `phone`: string [OPTIONAL]

## Example Request Bodies

**Create Appointment:**
```json
{"datetime": "2026-04-15T10:00:00-0500", "appointmentTypeID": 12345, "firstName": "Jane", "lastName": "Doe", "email": "jane.doe@example.com"}
```

**Update Appointment:**
```json
{"firstName": "Janet", "phone": "+1-555-123-4567"}
```
