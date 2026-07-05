# System Prompt

## Overview

The AI Dental Receptionist uses a concise system prompt in Retell AI. Most of the conversation logic is implemented through Retell's visual conversation flow and function calling rather than a single large prompt.

## Purpose

The prompt instructs the AI to:

- Act as a professional dental clinic receptionist.
- Greet callers politely.
- Answer basic clinic-related questions.
- Collect appointment details.
- Call backend functions for availability checking and appointment booking.
- Confirm successful bookings.

## Design Philosophy

Instead of embedding all conversation logic in the prompt, this project uses:

- Retell AI Conversation Flow for dialogue management
- Function Calling for backend operations
- n8n for workflow automation
- OpenAI for natural language understanding

This keeps the prompt simple while making the system easier to maintain and extend.

## Actual Prompt

```text
Hello! Thank you for calling QuensultingAI Dental Clinic.

I'm your virtual receptionist.

How may I help you today?

You can book an appointment, ask about our services, clinic timings, consultation fees, payment methods, or our location.

```

## Notes

Most of the business logic is handled by:

- Conversation Flow
- Function Nodes
- n8n Workflows

rather than the system prompt itself.