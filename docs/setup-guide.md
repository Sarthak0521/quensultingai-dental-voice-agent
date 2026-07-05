# Setup Guide

## Prerequisites

Before running the project, ensure you have:

* Retell AI account
* OpenAI API key
* n8n Cloud account
* Google Cloud project
* Google Calendar
* Google Sheets
* Gmail account

---

## Step 1: Configure Retell AI

* Create a Voice Agent.
* Add the system prompt.
* Configure webhook function.
* Connect the phone number.

---

## Step 2: Configure OpenAI

* Generate an API key.
* Add the API key to Retell AI or n8n as required.

---

## Step 3: Configure Google Calendar

* Create a dedicated calendar.
* Connect it to n8n using OAuth.
* Grant read/write permissions.

---

## Step 4: Configure Google Sheets

Create a sheet with the following columns:

* AppointmentID
* Name
* Phone
* Email
* Service
* Date
* Time
* Status
* Timestamp

Connect the sheet to n8n.

---

## Step 5: Configure Gmail

* Connect Gmail using OAuth.
* Enable email sending permissions.

---

## Step 6: Import n8n Workflow

1. Open n8n.
2. Click Import Workflow.
3. Select `workflows/n8n-workflow.json`.
4. Update all credentials.
5. Activate the workflow.

---

## Step 7: Test

Call the AI receptionist and verify:

* Appointment creation
* Calendar event
* Google Sheets record
* Confirmation email

The project is now ready for use.
