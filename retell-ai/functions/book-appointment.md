# Book Appointment Function

## Overview

The **Book Appointment** function is invoked by the Retell AI voice agent after all required appointment information has been collected and the requested appointment slot has been confirmed as available.

Instead of booking appointments directly, Retell AI delegates this responsibility to an n8n workflow through an HTTP webhook.

---

# Purpose

This function is responsible for:

- Sending appointment details to n8n
- Triggering the appointment booking workflow
- Creating a Google Calendar event
- Recording the appointment in Google Sheets
- Sending a confirmation email
- Returning the booking status to Retell AI

---

# Trigger Conditions

This function is called only after the AI has collected:

- Patient Name
- Phone Number
- Email Address
- Dental Service
- Appointment Date
- Appointment Time

The appointment must also be confirmed as **available** before this function is executed.

---

# Function Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| name | String | Yes | Patient's full name |
| phone | String | Yes | Mobile number |
| email | String | Yes | Email address |
| service | String | Yes | Selected dental service |
| date | String | Yes | Appointment date |
| time | String | Yes | Appointment time |

---

# Example Request

```json
{
  "name": "Rahul Sharma",
  "phone": "9876543210",
  "email": "rahul@example.com",
  "service": "General Dental Consultation",
  "date": "July 10, 2026",
  "time": "2:00 PM"
}
```

---

# Backend Workflow

After receiving the request, the n8n workflow performs the following actions:

1. Validate the received data.
2. Parse the appointment date and time.
3. Create a Google Calendar event.
4. Store the booking in Google Sheets.
5. Send a confirmation email.
6. Return the booking result.

---

# Success Response

Example:

```json
{
  "success": true,
  "message": "Appointment booked successfully."
}
```

---

# Failure Response

Example:

```json
{
  "success": false,
  "message": "Unable to book the appointment."
}
```

Possible reasons include:

- Invalid appointment data
- Calendar API error
- Google Sheets error
- Gmail delivery failure
- Internal workflow error

---

# Conversation Flow

```
Patient

↓

AI collects appointment details

↓

Book Appointment Function

↓

n8n Booking Workflow

↓

Google Calendar

↓

Google Sheets

↓

Gmail

↓

Booking Result

↓

Retell AI informs the patient
```

---

# Related Files

- `functions/check-availability.md`
- `n8n/docs/workflow-explanation.md`
- `docs/api-documentation.md`