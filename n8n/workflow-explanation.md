# n8n Workflow Explanation

# Overview

The AI Dental Receptionist uses **two independent n8n workflows**:

1. **Appointment Booking Workflow**
2. **Appointment Availability Workflow**

The Booking Workflow creates appointments after collecting patient details, while the Availability Workflow checks whether a requested appointment slot is available before booking.

---

# Workflow 1: Appointment Booking

## Purpose

This workflow receives appointment details from Retell AI and automates the complete booking process.

Responsibilities:

- Receive booking request
- Parse and validate date/time
- Create Google Calendar event
- Store appointment in Google Sheets
- Send confirmation email
- Return success response

---

## Workflow Diagram

```text
Retell AI

↓

Webhook

↓

Parse Date & Time

↓

Google Calendar

↓

Google Sheets

↓

Gmail

↓

Webhook Response
```

---

# Node 1 – Retell AI Webhook

## Purpose

Acts as the entry point for the workflow.

Retell AI sends an HTTP POST request containing all appointment details collected during the voice conversation.

---

### Input

Example request:

```json
{
  "name": "Rahul Sharma",
  "phone": "9876543210",
  "email": "rahul@gmail.com",
  "service": "General Dental Consultation",
  "date": "July 4, 2026",
  "time": "2:00 PM"
}
```

---

### Processing

- Receives JSON payload
- Starts workflow execution

---

### Output

Passes appointment information to the Parse Date & Time node.

---

# Node 2 – Parse Date & Time

## Purpose

Converts natural-language dates and 12-hour time into standardized ISO datetime values accepted by Google Calendar.

---

### Responsibilities

- Validate required fields
- Parse natural-language dates
- Convert 12-hour time to 24-hour format
- Create start datetime
- Calculate end datetime
- Handle invalid dates

---

### Input

```json
{
  "date":"July 4, 2026",
  "time":"2:00 PM"
}
```

---

### Processing

Example:

Input

```
July 4, 2026
2:00 PM
```

↓

Output

```
2026-07-04T14:00:00+05:30
```

---

### Output

```json
{
  "start":"2026-07-04T14:00:00+05:30",
  "end":"2026-07-04T15:00:00+05:30"
}
```

---

# Node 3 – Google Calendar

## Purpose

Creates the appointment inside the Dental Clinic Google Calendar.

---

### Responsibilities

- Create calendar event
- Add patient information
- Store event ID
- Reserve appointment slot

---

### Event Details

Title

```
General Dental Consultation - Rahul Sharma
```

Description

```
Phone
Email
Service
Appointment Details
```

Duration

```
1 Hour
```

---

### Output

Google Calendar returns

- Event ID
- Start Time
- End Time

Example

```json
{
   "eventId":"abc123xyz"
}
```

---

# Node 4 – Google Sheets

## Purpose

Stores appointment details for clinic staff.

---

### Spreadsheet Columns

| Column | Description |
|---------|-------------|
| AppointmentID | Unique booking ID |
| Name | Patient name |
| Phone | Mobile number |
| Service | Dental service |
| Date | Appointment date |
| Time | Appointment time |
| Status | Booking status |
| Timestamp | Booking creation time |
| Email | Patient email |
| CalendarEventID | Google Calendar Event ID |

---

### Responsibilities

Append one row after every successful booking.

---

### Output

Appointment record successfully saved.

---

# Node 5 – Gmail

## Purpose

Automatically sends booking confirmation to the patient.

---

### Email Subject

```
Dental Appointment Confirmation
```

---

### Email Includes

- Patient Name
- Service
- Appointment Date
- Appointment Time
- Clinic Information

---

### Example

```
Hello Rahul Sharma,

Your appointment has been successfully booked.

Service:
General Dental Consultation

Date:
4 July 2026

Time:
2:00 PM

Thank you.
```

---

### Output

Email delivered successfully.

---

# Node 6 – Return Success Response

## Purpose

Returns the final response back to Retell AI.

---

### Example Response

```json
{
    "success":true,
    "message":"Appointment booked successfully."
}
```

Retell AI converts this response into natural speech and informs the patient.

---

# Booking Workflow Summary

```
Patient

↓

Retell AI

↓

Webhook

↓

Parse Date

↓

Google Calendar

↓

Google Sheets

↓

Gmail

↓

Success Response

↓

Patient
```

---

# Workflow 2: Appointment Availability

## Purpose

Checks whether a requested appointment slot is already booked.

This workflow prevents double bookings.

---

## Workflow Diagram

```text
Retell AI

↓

Webhook

↓

Parse Date & Time

↓

Google Calendar

↓

JavaScript

↓

Webhook Response
```

---

# Node 1 – Retell AI Webhook

Receives

- Preferred Date
- Preferred Time

from Retell AI.

---

# Node 2 – Parse Date & Time

Converts the requested appointment into ISO datetime format.

Example

```
4 PM

↓

16:00
```

---

# Node 3 – Google Calendar

Retrieves all events within the requested time window.

---

### Processing

Searches

```
Start Time

↓

End Time
```

Returns

```
All Existing Appointments
```

---

# Node 4 – JavaScript Code Node

## Purpose

Determines whether the requested appointment overlaps with an existing booking.

---

### Responsibilities

- Compare requested slot
- Compare event start
- Compare event end
- Detect conflicts

---

### Example

Requested

```
4 PM – 5 PM
```

Existing

```
4 PM – 5 PM
```

↓

```
Unavailable
```

Requested

```
5 PM – 6 PM
```

↓

```
Available
```

---

### Output

```json
{
    "available":true
}
```

or

```json
{
    "available":false
}
```

---

# Node 5 – Respond to Webhook

Returns availability status to Retell AI.

Example

```json
{
   "available":false,
   "message":"Requested slot is unavailable."
}
```

Retell AI then asks the patient to choose another preferred appointment time.

---

# Availability Workflow Summary

```
Patient

↓

Retell AI

↓

Webhook

↓

Parse Date

↓

Google Calendar

↓

Availability Check

↓

Response

↓

Patient
```

---

# Error Handling

The workflows include validation for:

- Missing name
- Missing email
- Missing phone number
- Invalid date format
- Invalid time format
- Calendar conflicts
- Google API errors
- Email delivery failures

Whenever an error occurs, the workflow returns a descriptive response to Retell AI, allowing the voice agent to guide the patient toward corrective action.

---

# Overall System Flow

```
Patient
     │
     ▼
Retell AI Voice Agent
     │
     ▼
Availability Workflow
     │
     ▼
Available?
   │        │
 Yes        No
 │          │
 ▼          ▼
Booking     Ask for another time
Workflow
 │
 ▼
Google Calendar
 │
 ▼
Google Sheets
 │
 ▼
Gmail
 │
 ▼
Patient receives confirmation
```

---

# Key Integrations

| Service | Purpose |
|----------|---------|
| Retell AI | Voice conversation and function calling |
| n8n | Workflow orchestration |
| Google Calendar | Appointment scheduling |
| Google Sheets | Appointment database |
| Gmail | Confirmation emails |

---

# Conclusion

The AI Dental Receptionist automates the complete appointment booking lifecycle. By integrating conversational AI with workflow automation and Google Workspace services, the system minimizes manual effort, prevents scheduling conflicts, maintains centralized appointment records, and provides patients with immediate booking confirmations through an efficient end-to-end process.