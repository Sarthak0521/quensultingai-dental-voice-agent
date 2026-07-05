# Automation Workflow

## Retell AI Conversation Flow

The conversational logic is powered by **Retell AI**, which guides callers through the appointment booking process.

**Interactive Preview:**
https://agent.retellai.com/preview/agent_88a2275804f92d93ee640588b9

### Conversation Flow

* Welcome greeting
* Service selection
* Appointment date collection
* Appointment time collection
* Availability check
* Booking confirmation
* Error handling

---

# Booking Process

### Step 1 – Incoming Call

The patient calls the AI receptionist to schedule a dental appointment.

---

### Step 2 – Information Collection

The AI collects the following details:

* Patient name
* Phone number
* Email address
* Dental service requested
* Preferred appointment date
* Preferred appointment time

---

### Step 3 – Send Data to n8n

Retell AI sends the collected appointment details to an **n8n webhook** for processing.

---

### Step 4 – Data Validation

The workflow validates:

* Required fields
* Email format
* Appointment date
* Appointment time

---

### Step 5 – Availability Check

The workflow checks **Google Calendar** to determine whether the requested appointment slot is available.

---

### Step 6 – Appointment Confirmation

If the requested time slot is available, the workflow:

* Creates a Google Calendar event
* Stores the appointment in Google Sheets
* Sends a confirmation email to the patient

---

### Step 7 – Alternative Time Suggestion

If the requested slot is unavailable, the AI asks the patient to choose another available appointment time.

---

# Workflow Nodes

1. Webhook
2. Parse Date & Time
3. Availability Check
4. IF Node
5. Google Calendar
6. Google Sheets
7. Gmail
8. Return Response

---

# Error Handling

The workflow gracefully handles the following scenarios:

* Invalid appointment date
* Invalid appointment time
* Missing required information
* Calendar scheduling conflicts
* Google API failures
* Email delivery failures

Each error returns a clear, user-friendly response so the caller knows how to proceed.
