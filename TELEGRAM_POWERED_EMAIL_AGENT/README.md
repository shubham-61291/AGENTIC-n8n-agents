<div align="center">

# Telegram-Powered Email Handling Agent

### Manage Gmail through natural-language requests in a Telegram chat

[![n8n](https://img.shields.io/badge/automation-n8n-EA4B71?style=flat-square)](https://n8n.io/)
![Integrations](https://img.shields.io/badge/integrations-Telegram%20%7C%20Gmail-4B7BEC?style=flat-square)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](./LICENSE)

**AI model:** Google Gemini · **Workflow memory:** Simple Memory

</div>

## Overview

This workflow connects a Telegram bot with Gmail through an AI Agent powered by Google Gemini. A user describes an email task in Telegram; the agent interprets the request, uses conversational memory, and calls the configured Gmail tool for supported email actions. The workflow returns confirmations, summaries, or clarifying responses to the user in Telegram.

The project is designed around natural-language interaction, contextual continuity, privacy-conscious instructions, and professional email communication.

## Workflow sequence

| Component | Responsibility |
|---|---|
| **Telegram Trigger** | Listens for incoming Telegram messages and captures the user’s request. |
| **Google Gemini Chat Model** | Supplies language understanding and reasoning for the agent. |
| **AI Agent** | Interprets user intent and decides whether to call the Gmail tool or respond directly. Its system prompt emphasizes privacy, clarity, and professional communication. |
| **Simple Memory** | Retains conversational context; the documented session key is based on the Telegram user ID. |
| **Gmail Tool** | Carries out configured email actions. The project documentation describes use cases including composing, sending, reading, and replying to emails, including replies to the latest message. |
| **Send a text message** | Delivers the AI Agent’s output back to the user via Telegram. |

## Capabilities and examples

- **Compose and send:** “Send an email to example@domain.com with subject ‘Meeting Update’ and message ‘Rescheduled to 4 PM.’”
- **Reply to a recent email:** “Reply to my last email with ‘Received, thank you.’”
- **Send a structured update:** “Send email to manager@company.com with subject ‘Project Done’ and message ‘All tasks complete.’”
- **Context-aware interaction:** Use conversation memory to maintain continuity between requests.
- **Telegram confirmations:** Receive the agent’s response or confirmation directly in the chat.

The intended end-to-end interaction is: Telegram message → AI Agent interprets request → Gmail tool executes the email action → AI output is sent back to Telegram.

## Requirements

- n8n with Telegram Trigger, AI Agent, Gemini, Simple Memory, Gmail Tool, and Telegram messaging nodes used in the workflow.
- A Telegram bot and its n8n credential.
- Gmail OAuth2 authorization for the Gmail account.
- Google Gemini API credential.

## Setup

### 1. Import the workflow

Import [`telegram_connected_email_handling_agent.json`](./telegram_connected_email_handling_agent.json) via **Workflows → Import from File**.

### 2. Connect credentials

- **Telegram API:** connect your Telegram bot credential.
- **Gmail OAuth2:** authorize the Gmail account used for the email actions.
- **Google Gemini (PaLM/Gemini API):** add the API credential and bind it to the model node.

### 3. Configure placeholders

| Placeholder | Purpose |
|---|---|
| `YOUR_TELEGRAM_API_ID` / `YOUR_TELEGRAM_API_NAME` | Telegram bot credential reference. |
| `YOUR_GMAIL_CRED_ID` / `YOUR_GMAIL_CRED_NAME` | Gmail credential reference. |
| `YOUR_GEMINI_API_ID` / `YOUR_GEMINI_API_NAME` | Gemini credential reference. |
| `YOUR_WEBHOOK_ID` | Trigger-related value if required by your configured version. |

Public exports may have personal information or environment-specific values removed deliberately. Bind your own credentials in n8n and keep tokens and OAuth details out of version control.

### 4. Deploy and test

Deploy or activate the Telegram bot workflow and send a test request, such as the Meeting Update example above. Confirm that the appropriate Gmail action occurs and that the resulting confirmation arrives in Telegram. The project instructions recommend confirming email actions before sending to avoid miscommunication. The README lists webhook IDs for each trigger node among the values to review for the configured deployment.

## Security and privacy

- Keep Telegram bot tokens, Gmail OAuth credentials, and Gemini API keys in n8n Credentials or environment variables.
- Confirm the recipient and content before sending important messages.
- Restrict access to the Telegram bot and connected Gmail account appropriately.
- Avoid including confidential email content in logs or messages visible to unauthorized users.

## Demonstration

[**Watch the Telegram-powered email agent demo**](https://www.youtube.com/watch?v=cAWc6gxOVek&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=7)

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
