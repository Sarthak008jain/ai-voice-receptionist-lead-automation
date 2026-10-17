# AI Voice Receptionist & Lead Management Automation

An AI-powered receptionist prototype for coaching institutes that collects student enquiries and records structured lead information in Google Sheets using workflow automation.

## Project Overview

Coaching institutes receive enquiries about courses, fees, batches, and callbacks. This project demonstrates how an AI voice assistant can collect enquiry information and pass it through an automated workflow for structured lead management.

## Tech Stack

- **Vapi** — AI voice assistant and function calling
- **n8n** — Workflow automation and webhook handling
- **JavaScript** — Extracting and structuring tool-call data
- **Google Sheets** — Lead storage and tracking
- **HTTP POST Webhooks** — Communication between Vapi and n8n

## System Architecture
![n8n workflow overview](Screenshot%20%28414%29.png)
```text
Student / Parent
       |
       v
Vapi Voice Assistant (Aditi)
       |
       v
save_brief Function Tool
       |
       v
n8n POST Webhook
       |
       v
JavaScript Data Extraction
       |
       v
Edit Fields / Data Mapping
       |
       v
Google Sheets — Lead Record
```
![Google Sheets lead management output](Screenshot%20%28424%29.png)
## Features

- AI receptionist configured for coaching institute enquiries.
- Structured collection of student name, phone number, course interest, enquiry priority, and summary.
- Webhook-based communication between the assistant and automation workflow.
- JavaScript transformation of nested Vapi tool-call payloads into clean fields.
- Automated Google Sheets row creation with a generated lead ID and a default lead status.
- Separate fields for lead tracking and follow-up information.

## Example Lead Record

| Field | Example |
|---|---|
| Student Name | Sample Student |
| Phone | 9999999999 |
| Course Interest | CAT Coaching |
| Priority | High |
| Lead Status | New |
| AI Summary | Interested in the next batch and requested a callback. |

*All example information is fictional.*

## Workflow Implementation

1. Vapi sends a `save_brief` function tool call containing enquiry details.
2. The n8n webhook receives the incoming POST request.
3. A JavaScript Code node extracts the function arguments and creates a clean JSON object.
4. An Edit Fields node maps the extracted values.
5. The Google Sheets node appends a lead record to the spreadsheet.

## Testing and Validation

The workflow was tested using a captured webhook payload. The JavaScript extraction and field mapping produced the expected structured values, and the Google Sheets node successfully generated a row containing the mapped fields.

A fresh end-to-end test with a live assistant conversation should be completed to verify the full conversation-to-spreadsheet process.

## Learning Outcomes

- Designing webhook-driven automation workflows.
- Working with nested JSON payloads and JavaScript expressions.
- Integrating an AI assistant with external applications.
- Debugging field-mapping and data-transformation issues.
- Structuring lead data for operational tracking.

## Privacy and Security

This repository is intended to document the project. It does not contain API credentials or live student records. Credentials, API keys, private data, and production webhook URLs should be stored securely and excluded from public files.

## Future Improvements

- Caller identification and returning-student recognition.
- Google Calendar booking and callback scheduling.
- Automated notifications and follow-up reminders.
- Lead-management dashboard and reporting.
- Improved webhook authentication and error handling.

---

**Project Status:** Working prototype; live end-to-end validation and additional features are ongoing.

**Author:** Sarthak
