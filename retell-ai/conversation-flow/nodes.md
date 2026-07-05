# Conversation Flow Nodes

# Overview

This document explains the major nodes used in the Retell AI conversation flow.

The flow is designed to guide patients through appointment booking while maintaining a natural and professional conversation.

---

# Flow Summary

```
Greeting

↓

Understand User Request

↓

Collect Patient Information

↓

Check Availability

↓

Available?

├── Yes
│      ↓
│   Book Appointment
│      ↓
│   Confirm Booking
│
└── No
       ↓
Choose Another Time
```

---

# Node 1 – Greeting

## Purpose

Welcomes the patient and starts the conversation.

### Responsibilities

- Welcome the caller
- Introduce the clinic
- Ask how the AI can help

### Example

> Hello! Thank you for calling QuensultingAI Dental Clinic. How may I assist you today?

---

# Node 2 – Intent Identification

## Purpose

Determine why the caller contacted the clinic.

Supported intents include:

- Book Appointment
- Ask Clinic Hours
- Ask Available Services
- General Questions

Depending on the user's response, the conversation follows the appropriate branch.

---

# Node 3 – Collect Patient Name

## Purpose

Collect the patient's full name.

### Required

✅ Yes

Example

> May I have your full name, please?

---

# Node 4 – Collect Phone Number

## Purpose

Collect the patient's contact number.

### Required

✅ Yes

Example

> Could you please provide your mobile number?

---

# Node 5 – Collect Email Address

## Purpose

Collect the patient's email for confirmation.

### Required

✅ Yes

Example

> What email address should I send the appointment confirmation to?

---

# Node 6 – Select Dental Service

## Purpose

Identify which dental service the patient requires.

Supported services include:

- General Dental Consultation
- Dental Cleaning
- Teeth Whitening
- Root Canal Treatment
- Tooth Extraction
- Braces Consultation

---

# Node 7 – Collect Preferred Date

## Purpose

Ask the patient for their preferred appointment date.

Example

> Which date would you prefer for your appointment?

---

# Node 8 – Collect Preferred Time

## Purpose

Collect the preferred appointment time.

Example

> What time would you like to visit?

---

# Node 9 – Check Availability Function

## Purpose

Invoke the **Check Availability** function.

The function sends the requested date and time to the n8n Availability Workflow.

Possible outcomes:

- Available
- Unavailable

---

# Node 10 – Availability Decision

## If Available

Continue to booking.

## If Unavailable

Inform the patient.

Example

> That time is already booked. Would you like another appointment time?

The flow loops back to collect another preferred time.

---

# Node 11 – Book Appointment Function

## Purpose

Invoke the **Book Appointment** function.

The booking workflow:

- Creates Google Calendar Event
- Stores booking in Google Sheets
- Sends confirmation email

---

# Node 12 – Booking Confirmation

## Purpose

Inform the patient that the appointment has been booked successfully.

Example

> Your appointment has been confirmed. A confirmation email has been sent to your registered email address.

---

# Node 13 – General Questions

If the patient asks questions instead of booking, the AI answers using the configured clinic information.

Examples include:

- Clinic Hours
- Services
- Working Days

---

# Node 14 – Error Recovery

If information is missing or invalid, the AI requests only the missing information.

Examples

Missing email

↓

Ask for email

Missing phone number

↓

Ask for phone number

Invalid appointment time

↓

Ask for another time

---

# Node 15 – Conversation End

The conversation ends after:

- Successful booking
- User decides not to book
- Conversation completed

Example

> Thank you for calling QuensultingAI Dental Clinic. Have a wonderful day!

---

# Related Documentation

- prompts/system-prompt.md
- functions/check-availability.md
- functions/book-appointment.md
- ../../n8n/docs/workflow-explanation.md