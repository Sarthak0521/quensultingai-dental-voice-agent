# Design Decisions

## Why Retell AI?

Retell AI provides natural voice conversations with built-in support for conversational flows and function calling, making it suitable for voice-based appointment booking.

---

## Why n8n?

n8n enables visual workflow automation while integrating easily with external services such as Google Calendar, Google Sheets, Gmail, and OpenAI. It simplifies orchestration without requiring a custom backend.

---

## Why Google Calendar?

Google Calendar provides a reliable way to manage appointment schedules and helps prevent double bookings by checking availability before creating events.

---

## Why Google Sheets?

Google Sheets serves as a lightweight database for storing appointment records. It is easy to configure, accessible for clinic staff, and sufficient for small to medium-scale deployments.

---

## Why Gmail?

Gmail integration allows automated confirmation emails to be sent immediately after a successful booking, improving the patient experience.

---

## Scalability

For production deployments with higher traffic, the following improvements are recommended:

* Replace Google Sheets with PostgreSQL or MySQL.
* Add Redis for caching and queue management.
* Deploy n8n in queue mode for improved performance.
* Introduce authentication and rate limiting for webhook endpoints.
* Implement centralized logging and monitoring.

---

## Security Considerations

* Store API keys securely using environment variables or credential managers.
* Restrict access to webhook endpoints where possible.
* Use OAuth for Google integrations.
* Validate all incoming request data before processing.
