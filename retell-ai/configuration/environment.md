# Environment Configuration

# Overview

This document describes the external services and environment configuration required for the AI Dental Receptionist.

Sensitive information such as API keys and credentials should **never** be committed to the repository.

---

# External Services

The project integrates with the following services:

| Service | Purpose |
|----------|---------|
| Retell AI | Voice conversation |
| OpenAI | Natural language understanding |
| n8n | Workflow automation |
| Google Calendar | Appointment scheduling |
| Google Sheets | Booking records |
| Gmail | Confirmation emails |

---

# Required Credentials

Before running the project, configure the following credentials within Retell AI and n8n:

- OpenAI API Key
- Google OAuth Credentials
- Gmail OAuth Credentials
- Google Calendar Credentials
- Google Sheets Credentials

---

# Webhook Configuration

Retell AI communicates with n8n through HTTP webhooks.

The following workflows are exposed as webhook endpoints:

- Check Appointment Availability
- Book Appointment

The webhook URLs should be configured inside the Retell AI function definitions.

---

# Security Notes

To protect sensitive information:

- Do not commit API keys.
- Do not expose OAuth credentials.
- Do not publish webhook secrets.
- Use environment variables or secure credential storage.

---

# Deployment Notes

For production deployment, consider:

- HTTPS webhook endpoints
- OAuth credential rotation
- Rate limiting
- Workflow monitoring
- Error logging
- Backup of booking data

---

# Repository Guidelines

The repository intentionally excludes:

- API keys
- OAuth secrets
- Credential exports
- Personal patient information
- Internal webhook secrets

Only documentation, workflow definitions, and sample payloads are included.