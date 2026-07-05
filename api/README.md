# API Documentation

# Overview

The AI Dental Receptionist communicates with backend automation through HTTP webhooks.

Instead of a traditional REST API server, Retell AI invokes n8n workflows using function calls.

The project exposes two webhook endpoints:

1. Check Appointment Availability
2. Book Appointment

---

# API Flow

```
Patient

↓

Retell AI

↓

Function Call

↓

n8n Webhook

↓

Google Services

↓

Webhook Response

↓

Retell AI

↓

Patient
```

---

# Available Endpoints

| Endpoint | Purpose |
|----------|---------|
| Check Availability | Verify appointment availability |
| Book Appointment | Create a new appointment |

---

# Folder Structure

```
api/
│
├── requests/
├── responses/
├── webhooks/
└── postman/
```

---

# Related Documentation

- docs/api-documentation.md
- n8n/docs/workflow-explanation.md
- retell-ai/functions/