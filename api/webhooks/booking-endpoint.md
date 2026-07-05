# Booking Webhook

## Purpose

Creates a confirmed appointment after availability has been verified.

---

## Method

POST

---

## Called By

Retell AI Function Calling

---

## Request Body

```json
{
  "name":"Rahul Sharma",
  "phone":"9876543210",
  "email":"rahul@example.com",
  "service":"General Dental Consultation",
  "date":"July 10, 2026",
  "time":"2:00 PM"
}
```

---

## Workflow

Retell AI

↓

n8n Booking Workflow

↓

Create Calendar Event

↓

Store in Google Sheets

↓

Send Email

↓

Return Success

---

## Success Response

```json
{
    "success":true,
    "message":"Appointment booked successfully."
}
```

---

## Failure Response

```json
{
    "success":false,
    "message":"Unable to book appointment."
}
```

---

## Related Workflow

n8n Booking Workflow