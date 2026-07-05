# Retell AI Preview

## Overview

This project includes an interactive Retell AI conversation flow that demonstrates the complete behavior of the AI Dental Receptionist.

The preview allows reviewers to explore the conversation flow without importing the project into Retell AI.

---

# Interactive Preview
https://agent.retellai.com/preview/agent_88a2275804f92d93ee640588b9
```

---

# What the Preview Demonstrates

The interactive preview includes the complete conversation workflow:

- Greeting the patient
- Understanding the user's intent
- Collecting appointment details
- Checking appointment availability
- Booking appointments
- Handling unavailable appointment slots
- Confirming successful bookings
- Ending the conversation

---

# Features Demonstrated

## Natural Conversation

The AI maintains a professional and friendly conversational tone throughout the interaction.

---

## Information Collection

The AI gathers:

- Full Name
- Phone Number
- Email Address
- Dental Service
- Preferred Date
- Preferred Time

---

## Function Calling

The preview demonstrates two backend function calls:

### Check Availability

Checks Google Calendar for appointment conflicts.

### Book Appointment

Creates the appointment after availability is confirmed.

---

## Backend Integration

The Retell AI agent communicates with the following services through n8n:

- Google Calendar
- Google Sheets
- Gmail

---

# Notes

The preview represents the conversational layer only.

Backend operations are executed through n8n workflows and are documented separately in:

```
n8n/docs/workflow-explanation.md
```

---

# Screenshots

For static documentation, screenshots of the conversation flow are available in:

```
retell-ai/screenshots/
```

These screenshots complement the interactive preview and provide a quick visual overview of the flow.

---

# Related Documentation

- flow-overview.md
- nodes.md
- ../functions/book-appointment.md
- ../functions/check-availability.md
- ../../README.md