# API Documentation

## Booking Endpoint

### POST /book-appointment

Receives appointment details from the AI voice agent.

---

## Request Body

```json
{
  "name": "John Doe",
  "phone": "+919876543210",
  "email": "john@example.com",
  "service": "Dental Cleaning",
  "date": "2026-07-10",
  "time": "10:00 AM"
}
```

---

## Success Response

```json
{
  "success": true,
  "message": "Appointment booked successfully.",
  "appointmentId": "APT-001"
}
```

---

## Failure Response

```json
{
  "success": false,
  "message": "Requested slot is unavailable."
}
```

---

## Validation Rules

* Name is required.
* Phone number is required.
* Email must be valid.
* Service is required.
* Date must not be in the past.
* Time must fall within clinic working hours.

---

## HTTP Status Codes

| Status | Meaning               |
| ------ | --------------------- |
| 200    | Booking successful    |
| 400    | Invalid request       |
| 409    | Time slot unavailable |
| 500    | Internal server error |
