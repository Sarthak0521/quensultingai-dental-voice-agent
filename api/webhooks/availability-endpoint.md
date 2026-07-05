# Availability Webhook

## Purpose

Checks whether a requested appointment slot is available.

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
    "date":"July 10, 2026",
    "time":"2:00 PM"
}
```

---

## Workflow

Retell AI

↓

n8n Webhook

↓

Parse Date

↓

Google Calendar

↓

Availability Check

↓

Response

---

## Success Response

```json
{
    "available":true
}
```

---

## Failure Response

```json
{
    "available":false
}
```

---

## Related Workflow

n8n Availability Workflow