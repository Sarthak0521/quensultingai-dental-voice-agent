# Conversation Flow Overview

# Overview

The AI Dental Receptionist is designed to simulate a professional front-desk receptionist for a dental clinic. The conversation flow guides callers through appointment booking while ensuring all required information is collected before interacting with backend services.

Instead of relying on one large prompt, the conversational logic is implemented using **Retell AI's visual conversation flow**, **function calling**, and **n8n automation workflows**.

---

# Conversation Objectives

The conversation flow is designed to:

- Welcome patients professionally
- Understand the caller's intent
- Answer basic clinic-related questions
- Collect appointment details
- Check appointment availability
- Book appointments
- Confirm successful bookings
- Handle unavailable appointment slots gracefully

---

# High-Level Flow

```
Patient Calls

↓

Greeting

↓

Understand User Intent

↓

Appointment Booking?

│

├── Yes

│      ↓

│   Collect Patient Information

│      ↓

│   Check Appointment Availability

│      ↓

│   Available?

│      │

│      ├── Yes

│      │      ↓

│      │   Book Appointment

│      │      ↓

│      │   Send Confirmation

│      │      ↓

│      │   End Conversation

│      │

│      └── No

│             ↓

│      Ask for Another Time

│             ↓

│      Check Availability Again

│

└── General Questions

        ↓

Provide Clinic Information

↓

End Conversation
```

---

# Stage 1 – Greeting

The conversation begins with a friendly welcome message.

Example:

> "Hello! Thank you for calling QuensultingAI Dental Clinic. How may I assist you today?"

The objective is to establish a natural and professional interaction.

---

# Stage 2 – Intent Detection

The AI determines why the caller has contacted the clinic.

Typical intents include:

- Book an appointment
- Ask about clinic services
- Ask about working hours
- Request general information

If the caller wants to schedule an appointment, the booking flow begins.

---

# Stage 3 – Information Collection

Before any booking can occur, the AI collects the required patient information.

Required information includes:

- Full Name
- Mobile Number
- Email Address
- Dental Service
- Preferred Appointment Date
- Preferred Appointment Time

Each field is collected conversationally rather than asking multiple questions at once.

---

# Stage 4 – Availability Check

Once the preferred date and time have been collected, the AI invokes the **Check Availability** function.

The request is sent to the n8n Availability Workflow, which queries Google Calendar for conflicting appointments.

Possible outcomes:

### Slot Available

The conversation continues to appointment booking.

### Slot Unavailable

The AI politely informs the patient that the requested slot is unavailable and asks them to choose another date or time.

---

# Stage 5 – Appointment Booking

If the requested appointment slot is available, the AI invokes the **Book Appointment** function.

The n8n Booking Workflow then:

- Creates a Google Calendar event
- Records the appointment in Google Sheets
- Sends a confirmation email
- Returns a success response

---

# Stage 6 – Booking Confirmation

After the booking workflow completes successfully, the AI confirms the appointment.

Example:

> "Your appointment has been successfully booked. A confirmation email has been sent to your registered email address. We look forward to seeing you."

---

# Alternative Conversation Paths

## Unavailable Appointment

If the requested appointment time is unavailable:

- Inform the patient
- Request another preferred date or time
- Repeat the availability check

The conversation continues until a valid appointment slot is selected or the caller chooses to end the conversation.

---

## Missing Information

If required information is missing, the AI asks only for the missing field instead of restarting the booking process.

Example:

Missing email address:

> "May I also have your email address so I can send your appointment confirmation?"

---

## General Questions

If the caller asks about clinic information instead of booking an appointment, the AI answers using the configured clinic information.

Examples include:

- Working hours
- Available dental services
- Clinic schedule

---

# Backend Interaction

The conversation flow communicates with the backend through two function calls.

| Function | Purpose |
|----------|---------|
| Check Availability | Verify appointment availability |
| Book Appointment | Create a confirmed appointment |

Both functions are implemented using n8n workflows.

---

# Conversation Principles

The flow follows several design principles:

- Friendly and professional communication
- One question at a time
- Confirmation before booking
- No assumptions about missing information
- Function calls only when sufficient information has been collected
- Clear success and failure messages

---

# Related Documentation

- `../prompts/system-prompt.md`
- `../functions/check-availability.md`
- `../functions/book-appointment.md`
- `../../n8n/docs/workflow-explanation.md`