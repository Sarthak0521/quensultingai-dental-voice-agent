# LLM Settings

# Overview

The conversational intelligence of the AI Dental Receptionist is powered by a Large Language Model (LLM) configured within Retell AI.

This document describes the model configuration used for the project.

---

# Model Configuration

| Setting | Value |
|----------|-------|
| Model | *(Your Model Name)* |
| Temperature | *(Your Value)* |
| Max Tokens | *(Your Value)* |

Replace the above values with your actual Retell AI configuration.

---

# Responsibilities

The LLM is responsible for:

- Understanding user intent
- Managing conversations
- Asking follow-up questions
- Calling backend functions
- Handling unexpected responses
- Producing natural replies

---

# Prompt Strategy

Instead of embedding all business logic into the system prompt, the project separates responsibilities across:

- System Prompt
- Retell Conversation Flow
- Function Calling
- n8n Automation

This modular architecture improves maintainability and simplifies future updates.

---

# Function Calling

The LLM invokes two backend functions:

- Check Availability
- Book Appointment

The LLM waits for the function response before continuing the conversation.

---

# Error Recovery

If the model receives incomplete information, it requests only the missing field instead of restarting the conversation.

Examples include:

- Missing email
- Missing phone number
- Invalid appointment time
- Invalid appointment date

---

# Future Improvements

Potential enhancements include:

- Better intent classification
- Multilingual support
- Personalized conversations
- Context persistence across sessions