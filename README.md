<div align="center">
# 🎥 Live Demo

### 🎬 Loom Walkthrough

👉 https://www.loom.com/share/722af93a63854d50aa9cf348d4aaab42

🎙️ **Retell AI Interactive Preview:**  
👉 https://agent.retellai.com/preview/agent_88a2275804f92d93ee640588b9
# 🦷 AI Voice Receptionist for QuensultingAI Dental Clinic

### AI-powered voice receptionist for automated appointment booking using Retell AI, n8n, Google Calendar, Google Sheets, Gmail, and OpenAI.

![Retell AI](https://img.shields.io/badge/Retell-AI-blue?style=for-the-badge)
![n8n](https://img.shields.io/badge/n8n-Workflow_Automation-orange?style=for-the-badge)
![OpenAI](https://img.shields.io/badge/OpenAI-LLM-green?style=for-the-badge)
![Google Calendar](https://img.shields.io/badge/Google-Calendar-success?style=for-the-badge)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6-yellow?style=for-the-badge)

</div>

---

# 📖 Overview

This project is an **AI-powered voice receptionist** designed for **QuensultingAI Dental Clinic**.

The assistant automates the complete appointment booking process through natural voice conversations while integrating with Google services for scheduling and patient communication.

Instead of requiring a human receptionist for every booking, the AI can:

- Answer clinic-related questions
- Book appointments conversationally
- Check appointment availability
- Prevent scheduling conflicts
- Create Google Calendar events
- Store appointment details in Google Sheets
- Send confirmation emails automatically

The solution combines conversational AI with workflow automation to deliver a seamless booking experience.

---

# ✨ Features

## 🎙️ AI Voice Receptionist

- Human-like voice conversations
- Natural multi-turn dialogue
- Friendly appointment booking experience

---

## 📅 Appointment Booking

The assistant collects:

- Full Name
- Mobile Number
- Email Address
- Dental Service
- Preferred Appointment Date
- Preferred Appointment Time

---

## ⏰ Appointment Availability Checking

Before booking, the system:

- Checks Google Calendar
- Detects scheduling conflicts
- Prevents double-booking
- Requests another time if the slot is unavailable

---

## 📆 Google Calendar Integration

Automatically creates appointments including:

- Patient Name
- Dental Service
- Date
- Time
- Appointment Duration

---

## 📊 Google Sheets Integration

Stores every appointment with:

- Appointment ID
- Patient Name
- Phone Number
- Email Address
- Service
- Date
- Time
- Booking Status
- Timestamp

---

## 📧 Email Confirmation

After successful booking, the patient automatically receives an email containing:

- Appointment Date
- Appointment Time
- Selected Service
- Clinic Information

---

## 🏥 Clinic Information Assistant

The AI answers questions regarding:

- Working Hours
- Available Services
- Consultation Fee
- Payment Methods
- Clinic Address
- Walk-ins
- Emergency Appointments

---

# 🏗️ System Architecture

```text
                           Patient

                              │

                              ▼

                  Retell AI Voice Agent

                              │

                     Conversation Flow

                              │

               Custom Functions (API Calls)

                              │

                              ▼

                        n8n Workflows

              ┌──────────────┼──────────────┐
              │              │              │
              ▼              ▼              ▼

      Google Calendar   Google Sheets    Gmail

              │
              ▼

      Appointment Confirmation
```

---

# 🔄 Appointment Booking Workflow

```text
Caller

↓

Greets AI Receptionist

↓

Collect Patient Information

↓

Check Appointment Availability

↓

Available?

├── Yes
│
├── Create Google Calendar Event
│
├── Store in Google Sheets
│
├── Send Confirmation Email
│
└── Booking Successful

└── No

↓

Request Another Date/Time

↓

Repeat Availability Check
```

---

# 💻 Tech Stack

| Technology | Purpose |
|------------|----------|
| Retell AI | Voice Agent |
| n8n | Workflow Automation |
| OpenAI | Conversational Intelligence |
| Google Calendar API | Appointment Scheduling |
| Google Sheets API | Appointment Storage |
| Gmail API | Confirmation Emails |
| JavaScript | Workflow Logic |

---

# 📂 Project Structure

```text
quensultingai-dental-voice-agent/

├── api/
├── assets/
├── docs/
├── n8n/
├── retell-ai/
├── README.md
└── LICENSE
```

---

# ⚙️ Workflow Overview

## Retell AI

Responsible for:

- Handling voice conversations
- Collecting patient details
- Answering clinic queries
- Calling backend automation

---

## n8n

Responsible for:

- Parsing date & time
- Checking appointment availability
- Creating Google Calendar events
- Updating Google Sheets
- Sending confirmation emails

---

## Google Calendar

Acts as the appointment scheduling system.

---

## Google Sheets

Maintains appointment records.

---

## Gmail

Automatically sends confirmation emails after successful bookings.

---

# 📸 Screenshots

This repository includes screenshots of:

- Retell Conversation Flow
- Appointment Booking Workflow
- Availability Workflow
- Google Calendar Events
- Google Sheets Records
- Confirmation Email
- Voice Conversation

---

# 🚀 Future Improvements

- Appointment Rescheduling
- Appointment Cancellation
- WhatsApp Notifications
- SMS Reminders
- Online Payments
- Multi-doctor Scheduling
- CRM Integration
- Patient Portal
- Analytics Dashboard

---

# 🎥 Demo

The demonstration includes:

- Voice Conversation
- Appointment Booking
- Availability Check
- Google Calendar Integration
- Google Sheets Logging
- Email Confirmation

---

# 👨‍💻 Author

**Sarthak Patil**

Final Year B.Tech Student | Artificial Intelligence & Analytics

Interested in:

- Artificial Intelligence
- Agentic AI
- Voice AI
- Backend Development
- Workflow Automation
- System Design

---

## ⭐ Acknowledgements

This project was developed as part of an AI Voice Agent internship assignment to demonstrate conversational AI, workflow automation, and cloud integration for real-world appointment management.