<div align="center">

# Automatic Email Labelling and Reply Agent

### Classify Gmail messages, apply labels, and respond to sales enquiries

[![n8n](https://img.shields.io/badge/automation-n8n-EA4B71?style=flat-square)](https://n8n.io/)
![Integrations](https://img.shields.io/badge/integrations-Gmail%20%7C%20Gemini-4B7BEC?style=flat-square)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](./LICENSE)

</div>

## Overview

This workflow reads unread Gmail messages, classifies each email into **SALES**, **PROMOTION**, or **OTHER**, applies the matching Gmail label, and generates a tailored reply for sales-related messages. Gmail handles the trigger, labelling, and reply operations; Google Gemini powers the classifier and response-writing agent.

The routing deliberately treats categories differently: **SALES** emails receive a label and an AI-generated response, while **PROMOTION** and **OTHER** emails are labelled without sending a reply.

## Routing logic

| Classification | Examples / intent | Workflow action |
|---|---|---|
| **SALES** | Leads, quote requests, pricing questions, orders, purchase requests, and business enquiries. | Apply the Sales label, prepare a personalized reply, and use Gmail’s reply operation to send it. |
| **PROMOTION** | Offers, discounts, promotions, and newsletters. | Apply the Promotion label; no reply is sent. |
| **OTHER** | Support, personal, miscellaneous, and other messages that do not match the first two categories. | Apply the Other label; no reply is sent. |

The classifier receives the email’s subject and body. A switch routes the classification to the appropriate Gmail label node. The sales branch passes the source email context into a tailored-response agent, then connects the response to **Reply to a message**.

## Sales reply behavior

For sales-related inquiries, the response agent is instructed to identify the sender’s name when available, extract the stated pain point and industry/use case, and prepare a personalized response. The project describes the reply as including the lead’s name, requirement, and a meeting-scheduling link. Configure the response instructions and scheduling link to match your organization’s real offering; do not rely on a generic model response to supply factual business commitments.

## Workflow components

- **Gmail Trigger:** starts the workflow for unread messages.
- **Google Gemini Chat Model:** supports both email classification and reply drafting.
- **Email label classifier (AI Agent):** returns one of the documented categories.
- **Switch:** routes SALES, PROMOTION, and OTHER results.
- **Gmail label nodes:** apply the category-specific labels.
- **No Operation nodes:** end the PROMOTION and OTHER branches after labelling.
- **Tailored response (AI Agent):** drafts the response for the SALES path.
- **Reply to a message:** sends the prepared reply in the existing Gmail conversation.

## Requirements

- n8n.
- Gmail access and credentials configured in n8n.
- Google Gemini API access.
- Gmail labels for Sales, Promotion, and Other.
- The real meeting form or scheduling URL to include in the configured sales reply.

## Setup

### 1. Import the workflow

Import [`automatic_email_reading_label_&_reply.json`](./automatic_email_reading_label_&_reply.json) via **Workflows → Import from File**.

### 2. Configure Gmail and Gemini

Connect Gmail credentials to the Gmail Trigger, label operations, and Reply to a message node. Configure the Google Gemini credential on the chat-model node used by both AI agents.

### 3. Replace environment-specific values

| Placeholder | Purpose |
|---|---|
| `YOUR_SALES_LABEL_ID` | Gmail label ID for Sales. |
| `YOUR_PROMOTION_LABEL_ID` | Gmail label ID for Promotion. |
| `YOUR_OTHER_LABEL_ID` | Gmail label ID for Other. |
| `YOUR_API_KEY` | Gemini API key or credential value, as applicable to your configured environment. |
| `YOUR_MEETING_FORM_LINK` | Your actual meeting-scheduling link or form. |
| `YOUR_WEBHOOK_PLACEHOLDER` | The relevant n8n webhook ID or URL if used by your deployment. |

The public JSON has been sanitized for sharing. Configure your own account-specific values in n8n; do not commit real API keys, OAuth tokens, or private identifiers.

### 4. Run and validate

Start the workflow or configure it to run according to your n8n deployment. Send test messages for each category and check that the workflow applies the expected label. Verify that SALES messages receive a relevant reply, while PROMOTION and OTHER messages are labelled without a reply.

## Security and operating guidance

- Keep Gmail OAuth credentials and Gemini API keys in n8n Credentials or environment variables.
- Review the sales-response prompt and meeting link so that generated replies accurately represent your business.
- Test label IDs against a non-critical mailbox before rolling the automation out to a primary inbox.

## Possible extensions

- Log responses to Google Sheets or a CRM.
- Add spam filtering for unwanted messages.
- Improve reply templates with more personalized messaging.

## Demonstration

[**Watch the automatic email labelling and reply demo**](https://www.youtube.com/watch?v=oTsM5ict2xc&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1)

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
