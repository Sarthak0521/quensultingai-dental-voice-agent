# n8n Workflows

This folder contains the automation workflows used by the AI Dental Receptionist.

## Workflows

### book-appointment.json

Responsible for:

- Receiving booking requests
- Parsing date & time
- Creating Google Calendar events
- Logging appointments
- Sending confirmation emails

### check-availability.json

Responsible for:

- Receiving availability requests
- Checking Google Calendar
- Returning availability status