Sales Calling & Meeting Scheduling Agent (n8n + Retell AI)

This agent automates sales outreach and meeting scheduling using n8n + Retell AI.
It fetches lead details from Google Sheets, passes them to Retell AI, and Retell's conversational agent handles the actual call flow — including capturing requirements and scheduling meetings.

Features

Fetches lead details (name, email, phone, issue) from Google Sheets.

Initiates automated outbound calls via Retell AI.

Provides Retell agent with dynamic context (lead name, requirement, contact info).

Retell AI agent manages the conversation:
• Introduces your company/product
• Understands the lead’s requirements
• Offers to schedule a meeting/demo on the spot

Extensible → results can be logged back into Sheets or your CRM.

Files

sales_calling_agent_n8n.json → n8n workflow export.

Setup Instructions

Import Workflow

In n8n, go to Workflows → Import from File.

Upload sales_calling_agent_n8n.json.

Google Sheets Setup

Replace YOUR_SHEET_ID and YOUR_SHEET_NAME in the workflow.

Ensure the sheet includes: NAME, EMAIL ADD, MOBILE NUMBER, ISSUE.

Retell AI Setup

Replace placeholders:
• YOUR_API_KEY → Retell AI key
• FROM_NUMBER_PLACEHOLDER → your caller ID
• AGENT_ID_PLACEHOLDER → your Retell agent ID

Make sure your Retell agent is trained/configured to schedule meetings.

Run

Trigger manually or schedule with Cron in n8n.

For each lead row, Retell AI will place a call and attempt to schedule a meeting.

Security

Never commit real API keys or sheet IDs.

Use environment variables in n8n for production.

Next Steps

Write call outcomes (meeting scheduled, status, notes) back into Google Sheets.

Add CRM integration (HubSpot, Salesforce).

Extend with follow-up email automation after the call.

DEMO VIDEO : - https://www.youtube.com/watch?v=e_3sMgFad9E&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=3

Author
Shubham Singh

License
MIT License
