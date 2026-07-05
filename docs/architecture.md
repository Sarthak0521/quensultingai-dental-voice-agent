# System Architecture

## Overview

The AI Dental Receptionist is an intelligent voice-based appointment booking system that automates patient interactions using conversational AI and workflow automation.

The solution integrates Retell AI, OpenAI, n8n, Google Calendar, Google Sheets, and Gmail to create a seamless booking experience.

---

## Architecture Diagram

```
Patient
   │
   ▼
Retell AI Voice Agent
   │
   ▼
OpenAI (Conversation Intelligence)
   │
   ▼
n8n Automation
   │
   ├──────────────► Google Calendar
   │                   │
   │                   ▼
   │            Create Appointment
   │
   ├──────────────► Google Sheets
   │                   │
   │                   ▼
   │            Store Booking Record
   │
   └──────────────► Gmail
                       │
                       ▼
               Send Confirmation Email
```

---

## Components

### Retell AI

Responsible for:

* Receiving phone calls
* Managing conversation flow
* Collecting appointment details
* Calling backend webhook

---

### OpenAI

Responsible for:

* Natural language understanding
* Response generation
* Intent detection
* Handling user questions

---

### n8n

Acts as the orchestration layer.

Responsibilities include:

* Receiving webhook requests
* Validating user data
* Parsing date and time
* Checking appointment availability
* Creating calendar events
* Logging appointments
* Sending confirmation emails

---

### Google Calendar

Stores all confirmed appointments.

Each booking contains:

* Patient Name
* Service
* Date
* Time
* Email

---

### Google Sheets

Maintains a booking database.

Columns include:

* Appointment ID
* Name
* Phone
* Email
* Service
* Date
* Time
* Status
* Timestamp

---

### Gmail

Automatically sends appointment confirmation emails after successful booking.

---

## Workflow Summary

1. User calls the AI receptionist.
2. AI collects booking information.
3. Data is sent to n8n.
4. n8n validates inputs.
5. Calendar availability is checked.
6. Appointment is created.
7. Booking is stored in Google Sheets.
8. Confirmation email is sent.
9. AI confirms the booking to the caller.

---

## Technology Stack

| Component   | Technology                  |
| ----------- | --------------------------- |
| Voice Agent | Retell AI                   |
| LLM         | OpenAI GPT                  |
| Automation  | n8n                         |
| Calendar    | Google Calendar             |
| Database    | Google Sheets               |
| Email       | Gmail                       |
| Language    | JavaScript (n8n Code Nodes) |
