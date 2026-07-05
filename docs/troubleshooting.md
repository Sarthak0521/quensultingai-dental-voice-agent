# Troubleshooting

## Webhook Not Triggering

### Cause

The webhook URL is incorrect or the workflow is inactive.

### Solution

* Verify the webhook URL.
* Activate the n8n workflow.
* Test using the production webhook.

---

## Invalid Date Error

### Cause

The provided date format is unsupported.

### Solution

* Accept both ISO and natural-language dates.
* Validate the parsed date before creating the appointment.

---

## Google Calendar Authentication Error

### Cause

OAuth credentials are missing or expired.

### Solution

Reconnect the Google Calendar account and refresh the OAuth credentials.

---

## Gmail Email Not Sent

### Cause

The Gmail node is incorrectly configured.

### Solution

* Verify OAuth permissions.
* Ensure the recipient email field is populated.
* Test the Gmail node independently.

---

## Google Sheets Data Missing

### Cause

Incorrect column mapping.

### Solution

Check that each workflow field is mapped to the appropriate spreadsheet column.

---

## Appointment Conflict

### Cause

The requested time slot is already booked.

### Solution

Prompt the caller to choose another available date or time.

---

## Debugging Tips

* Review the execution history in n8n.
* Enable detailed logging during testing.
* Test each node individually before running the complete workflow.
* Verify Google API credentials after any account or permission changes.
