# Retell AI Configuration

## Overview

The conversational layer of the AI Dental Receptionist is implemented using **Retell AI**. It manages the complete voice interaction with patients, gathers appointment information, invokes backend workflows through function calls, and communicates booking results naturally.

This folder contains all documentation related to the Retell AI configuration used in this project.

---

# Responsibilities

The Retell AI agent is responsible for:

- Greeting callers
- Understanding natural language
- Collecting appointment information
- Calling n8n workflows through function calls
- Handling unavailable appointment slots
- Confirming successful bookings
- Responding to patient questions

---

# Folder Structure

```
retell-ai/
│
├── prompts/
├── functions/
├── conversation-flow/
├── configuration/
└── screenshots/
```

---

# Conversation Lifecycle

```
Patient

↓

Greeting

↓

Collect Patient Details

↓

Check Availability

↓

Available?

├── Yes
│      ↓
│   Book Appointment
│      ↓
│   Confirmation
│
└── No
       ↓
Suggest Another Time
```

---

# Function Calls

The agent currently invokes two backend functions.

| Function | Purpose |
|----------|---------|
| Check Availability | Verify whether the requested slot is free |
| Book Appointment | Create the appointment after availability confirmation |

---

# Integrations

The Retell AI agent communicates with:

- OpenAI GPT
- n8n
- Google Calendar
- Google Sheets
- Gmail

---

# Documentation

| File | Description |
|------|-------------|
| prompts/ | AI prompts used by the receptionist |
| functions/ | Function call documentation |
| conversation-flow/ | Flow explanation |
| configuration/ | Voice and model configuration |

---

# Screenshots

Store screenshots of:

- Agent configuration
- Conversation flow
- Booking function
- Availability function

inside the `screenshots/` folder.

---

# Preview

A live preview of the conversation flow is available in:

```
conversation-flow/preview-link.md
```