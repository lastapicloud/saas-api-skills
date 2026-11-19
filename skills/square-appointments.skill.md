---
name: square-appointments
description: Appointment booking and management via Square. Use when the user mentions square appointments, booking, schedule, salon, spa, fitness.
version: 1.0.0
skill_type: external
base_url_env: SQUARE_BASE_URL
auth_env_var: SQUARE_ACCESS_TOKEN
auth_type: bearer
triggers:
  - square appointments
  - square booking
  - schedule
  - salon
  - spa
  - fitness
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://developer.squareup.com/docs/bookings-api
---

# Square-Appointments

Appointment booking and management via Square. Use when the user mentions square appointments, booking, schedule, salon, spa, fitness.

## API Endpoints

- **GET** `/v2/bookings` - List bookings
- **POST** `/v2/bookings` - Create booking
- **GET** `/v2/bookings/{bookingId}` - Get booking
- **PATCH** `/v2/bookings/{bookingId}` - Update booking
- **DELETE** `/v2/bookings/{bookingId}` - Cancel booking
- **GET** `/v2/bookables` - List bookable resources
- **GET** `/v2/bookables/{bookableId}` - Get bookable resource
- **GET** `/v2/appointment-segments` - List appointment segments
- **GET** `/v2/business-hours` - Get business hours
- **PUT** `/v2/business-hours` - Update business hours

## Actions

- list_bookings: List bookings (GET /v2/bookings)
- create_booking: Create booking (POST /v2/bookings)
- get_booking: Get booking (GET /v2/bookings/{bookingId})
- update_booking: Update booking (PATCH /v2/bookings/{bookingId})
- cancel_booking: Cancel booking (DELETE /v2/bookings/{bookingId})
- list_bookables: List bookable resources (GET /v2/bookables)
- get_bookable: Get bookable resource (GET /v2/bookables/{bookableId})
- list_appointment_segments: List appointment segments (GET /v2/appointment-segments)
- get_business_hours: Get business hours (GET /v2/business-hours)
- update_business_hours: Update business hours (PUT /v2/business-hours)

## Fields

- `location_id`: string [REQUIRED] - Location ID
- `booking_id`: string [REQUIRED for get/update/cancel] - Booking ID
- `customer_id`: string [REQUIRED for create] - Customer ID
- `appointment_segments`: array [REQUIRED for create] - Appointment segments
- `start_at`: string [REQUIRED for create] - Start time (ISO 8601)
- `notes`: string [OPTIONAL] - Booking notes

## Example Request Bodies

**Create Booking:**
```json
{"location_id": "LOCATION_ID", "customer_id": "CUSTOMER_ID", "appointment_segments": [{"service_id": "SERVICE_ID", "staff_id": "STAFF_ID", "duration_minutes": 60}], "start_at": "2024-01-15T10:00:00Z"}
```

**Update Booking:**
```json
{"start_at": "2024-01-15T11:00:00Z", "notes": "Updated notes"}
```
