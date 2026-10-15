<div align="center">

# Sales Calling and Meeting Scheduling Agent

### Automate outbound lead calls using n8n, Google Sheets, and Retell AI

[![n8n](https://img.shields.io/badge/automation-n8n-EA4B71?style=flat-square)](https://n8n.io/)
[![Voice AI](https://img.shields.io/badge/voice%20AI-Retell-4B7BEC?style=flat-square)](https://www.retellai.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](./LICENSE)

</div>

## Overview

This workflow automates outbound sales outreach by reading lead details from Google Sheets and sending the call request to Retell AI. Retell’s configured conversational agent manages the live call: it introduces the company or product, uses the supplied lead context, understands the lead’s requirements, and offers to schedule a meeting or demo during the conversation.

The n8n workflow is intentionally straightforward: a manual trigger starts the process, Google Sheets provides the lead rows, and an HTTP Request node calls Retell AI’s `create-phone-call` endpoint.

## Workflow and call context

| Component | Responsibility |
|---|---|
| **Manual Trigger** | Starts the workflow when the operator clicks **Execute workflow**. The project also notes that a Cron trigger can be used for scheduled operation. |
| **Google Sheets — Get row(s) in sheet** | Retrieves lead data for the calling workflow. |
| **HTTP Request** | Sends the outbound-call request to Retell AI (`https://api.retellai.com/v2/create-phone-call`). |
| **Retell conversational agent** | Uses configured agent instructions and dynamic context to introduce the offering, understand the issue, and offer a meeting/demo. |

The lead context described in the project includes **name, email, phone number, and issue/requirement**. Retell’s agent is expected to use that context during the conversation.

## Expected Google Sheets columns

The original setup instructions specify these column labels:

- `NAME`
- `EMAIL ADD`
- `MOBILE NUMBER`
- `ISSUE`

Ensure the columns and mapping used in your workflow match the sheet containing the leads.

## Requirements

- n8n.
- A Google Sheet containing lead contact details.
- Google Sheets credentials configured in n8n.
- A Retell AI account, configured voice agent, API key, caller ID, and agent ID.
- A Retell agent prompt/profile configured to handle the desired sales conversation and meeting-scheduling flow.

## Setup

### 1. Import the workflow

Import [`sales_calling_agent_n8n.json`](./sales_calling_agent_n8n.json) through **Workflows → Import from File**.

### 2. Configure Google Sheets

Connect your Google Sheets credential. Set the sheet ID and sheet name, and confirm that the sheet includes the required `NAME`, `EMAIL ADD`, `MOBILE NUMBER`, and `ISSUE` fields.

### 3. Configure Retell AI

Supply the Retell API key, caller ID, and Retell agent ID using the appropriate n8n node parameters and credential mechanisms. The agent should be configured to introduce your company/product, understand the lead’s requirements, and offer a meeting or demo.

| Placeholder | Purpose |
|---|---|
| `YOUR_SHEET_ID` | Your Google spreadsheet ID. |
| `YOUR_SHEET_NAME` | Name of the sheet containing lead rows. |
| `YOUR_API_KEY` | Retell AI API key. |
| `FROM_NUMBER_PLACEHOLDER` | Configured caller ID / outbound number. |
| `AGENT_ID_PLACEHOLDER` | Retell conversational-agent ID. |

The public JSON is sanitized for sharing. Restore private values in your own n8n instance, and do not commit real API keys, phone numbers, or account identifiers.

### 4. Run or schedule

Run the workflow manually to test a small, controlled set of leads. The project notes that a Cron trigger can be used to schedule execution. Verify that the correct lead data reaches Retell and that the configured agent makes the intended outbound call.

## Results and possible extensions

The project describes meeting scheduling as part of the Retell agent’s conversation. The n8n workflow can be extended to write call outcomes—such as whether a meeting was scheduled, call status, and notes—back into Google Sheets or a CRM. Other suggested extensions include HubSpot/Salesforce integration and follow-up email automation.

## Security and operating guidance

- Keep Retell credentials and Google Sheets identifiers private; use n8n Credentials or environment variables in production.
- Test with controlled leads and ensure the call recipient and provided context are correct.
- Observe applicable consent, telemarketing, and calling rules for the regions in which you operate.
- Treat call outcomes and contact details as sensitive customer data.

## Demonstration

[**Watch the sales-calling and meeting-scheduling demo**](https://www.youtube.com/watch?v=e_3sMgFad9E&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=3)

## License

MIT License. See [`LICENSE`](./LICENSE). Full text:

### MIT License

MIT License

Copyright (c) 2026 Shubham Kumar Singh

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
