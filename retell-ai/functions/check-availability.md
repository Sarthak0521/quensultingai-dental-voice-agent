# Check Availability Function

## Overview

The **Check Availability** function is responsible for verifying whether the patient's requested appointment slot is available before a booking is created.

The Retell AI voice agent invokes this function through an HTTP webhook connected to an n8n workflow. The workflow checks Google Calendar for existing appointments and determines whether the requested time slot is free.

---

# Purpose

This function helps prevent double bookings by checking calendar availability before creating an appointment.

Responsibilities include:

- Receive the requested appointment date and time
- Convert the input into a standardized datetime format
- Query Google Calendar for overlapping events
- Determine whether the requested slot is available
- Return the availability status to Retell AI

---

# When is this Function Called?

The function is executed after the AI has collected:

- Preferred Appointment Date
- Preferred Appointment Time

The booking process continues only if the function returns that the slot is available.

---

# Function Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| date | String | Yes | Preferred appointment date |
| time | String | Yes | Preferred appointment time |

---

# Example Request

```json
{
  "date": "July 10, 2026",
  "time": "2:00 PM"
}
```

---

# Workflow Execution

Once the request reaches n8n, the workflow performs the following steps:

1. Receive the webhook request.
2. Parse the date and time.
3. Convert the values into ISO datetime format.
4. Query Google Calendar for events during the requested time.
5. Compare the requested slot with existing events.
6. Return the availability result.

---

# Success Response (Available)

```json
{
  "available": true,
  "message": "The requested appointment slot is available."
}
```

---

# Success Response (Unavailable)

```json
{
  "available": false,
  "message": "The requested appointment slot is unavailable."
}
```

---

# Possible Failure Response

```json
{
  "success": false,
  "message": "Unable to check appointment availability."
}
```

Possible reasons include:

- Invalid date format
- Invalid time format
- Google Calendar API error
- Workflow execution failure

---

# Conversation Flow

```
Patient

↓

Provides preferred date and time

↓

Retell AI

↓

Check Availability Function

↓

n8n Availability Workflow

↓

Google Calendar

↓

Availability Result

↓

Retell AI

↓

Available?
│
├── Yes → Continue to Book Appointment
│
└── No → Ask patient to choose another time
```

---

# Decision Logic

## If Available

- Inform the AI that the slot is free.
- Continue to the booking workflow.

---

## If Unavailable

The AI politely informs the patient that the requested slot is unavailable and asks for another preferred date or time.

No booking request is sent until an available slot is selected.

---

# Integration

This function communicates with:

| Service | Purpose |
|----------|---------|
| Retell AI | Initiates the function call |
| n8n | Processes the availability request |
| Google Calendar | Checks for conflicting appointments |

---

# Related Files

- `functions/book-appointment.md`
- `n8n/docs/workflow-explanation.md`
- `docs/api-documentation.md`