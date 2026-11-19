---
name: simplybook-appointments
description: Online appointment scheduling via SimplyBook.me. Use when the user mentions simplybook, booking, appointment, scheduler, service booking.
version: 1.0.0
skill_type: external
base_url_env: SIMPLYBOOK_BASE_URL
auth_env_var: SIMPLYBOOK_API_KEY
auth_type: bearer
triggers:
  - simplybook
  - simply book
  - booking
  - appointment
  - scheduler
  - service booking
license: Proprietary
metadata:
  author: lastapi
  version: 1.0.0
  documentation: https://help.simplybook.me/index.php/User_API_guide
---

# Simplybook-Appointments

Online appointment scheduling via SimplyBook.me. Use when the user mentions simplybook, booking, appointment, scheduler, service booking.

## API Endpoints

- **POST** `/json` - Get authentication token
- **POST** `/json` - Get company info
- **POST** `/json` - Get services list
- **POST** `/json` - Get service by ID
- **POST** `/json` - Get providers list
- **POST** `/json` - Get provider by ID
- **POST** `/json` - Get available time slots
- **POST** `/json` - Create booking
- **POST** `/json` - Get booking by ID
- **POST** `/json` - Update booking
- **POST** `/json` - Cancel booking
- **POST** `/json` - Get bookings list
- **POST** `/json` - Get categories list
- **POST** `/json` - Get custom fields

## Actions

- get_token: Get authentication token (POST /json)
- get_company_info: Get company info (POST /json)
- list_services: Get services list (POST /json)
- get_service: Get service by ID (POST /json)
- list_providers: Get providers list (POST /json)
- get_provider: Get provider by ID (POST /json)
- get_available_slots: Get available time slots (POST /json)
- create_booking: Create booking (POST /json)
- get_booking: Get booking by ID (POST /json)
- update_booking: Update booking (POST /json)
- cancel_booking: Cancel booking (POST /json)
- list_bookings: Get bookings list (POST /json)
- list_categories: Get categories list (POST /json)
- list_custom_fields: Get custom fields (POST /json)

## Fields

- `service_id`: integer [REQUIRED for booking] - Service ID
- `provider_id`: integer [REQUIRED for booking] - Provider/Staff ID
- `client_name`: string [REQUIRED for booking] - Client name
- `client_email`: string [REQUIRED for booking] - Client email
- `client_phone`: string [OPTIONAL] - Client phone
- `start_time`: string [REQUIRED for booking] - Start time (Y-m-d H:i:s)
- `end_time`: string [OPTIONAL] - End time
- `booking_id`: integer [REQUIRED for update/cancel] - Booking ID

## Example Request Bodies

**Get Available Slots:**
```json
{"method": "getAvailableTimeSlots", "params": {"service_id": 1, "provider_id": 1, "date": "2024-01-15"}}
```

**Create Booking:**
```json
{"method": "createBooking", "params": {"service_id": 1, "provider_id": 1, "client_name": "John Doe", "client_email": "john@example.com", "start_time": "2024-01-15 10:00:00"}}
```

**Cancel Booking:**
```json
{"method": "cancelBooking", "params": {"booking_id": 123}}
```
