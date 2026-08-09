# Voice-call
AI-powered outbound lead qualification agent built with n8n and Vapi, automating voice calls, lead validation, intent capture, qualification, and structured logging.
# 🤖 AI Voice Lead Qualification Agent

An end-to-end **AI-powered outbound lead qualification system** built with **n8n and Vapi** that automatically calls leads, captures qualification signals, and logs structured outcomes for sales follow-up.

## 🎯 What It Does

The workflow converts a form submission into a structured lead qualification process:

**Lead Form → Data Validation → AI Voice Call → Call Monitoring → Qualification → Structured Logging**

It automatically:

- Captures lead and company information
- Validates and standardizes phone numbers
- Initiates personalized outbound AI voice calls
- Monitors call completion
- Handles invalid numbers and voicemail scenarios
- Extracts structured qualification signals
- Logs call outcomes into Google Sheets

## 🧠 Qualification Signals

The AI voice agent captures:

- Service Interest
- Motivation
- Urgency
- Budget
- Past Experience
- Purchase Intent

This converts an unstructured voice conversation into structured lead data that can be used for prioritization and follow-up.

## ⚙️ Architecture

### 1. Lead Intake
An n8n form captures:

- Name
- Phone Number
- Email
- Company
- Role
- Request
- Company Size

### 2. Data Validation
A JavaScript node standardizes phone numbers and routes invalid entries separately.

### 3. AI Voice Call
n8n triggers the **Vapi API** and dynamically passes lead context to the AI voice assistant.

### 4. Call Monitoring
The workflow waits and polls the Vapi API until the call reaches completion.

### 5. Outcome Routing
Calls are automatically classified into outcomes such as:

- Completed
- Voicemail
- Invalid Phone Number

### 6. Lead Qualification
Structured outputs from the conversation capture key sales signals including intent, urgency and budget.

### 7. Structured Logging
Lead details, qualification signals and call status are automatically written to **Google Sheets**.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| **n8n** | Workflow orchestration |
| **Vapi** | AI voice calling |
| **JavaScript** | Data validation & transformation |
| **REST APIs** | Vapi integration |
| **Google Sheets** | Lead logging & tracking |

## 🔄 Workflow

```text
Form Submission
      ↓
Standardize Lead Data
      ↓
Validate Phone Number
      ↓
 ┌────┴─────┐
Invalid    Valid
   ↓          ↓
Log Error   AI Voice Call
              ↓
         Monitor Call
              ↓
         Call Completed?
              ↓
       ┌──────┴──────┐
   Voicemail      Completed
       ↓              ↓
 Log Callback    Extract Qualification
                      ↓
              Structured Lead Logging
