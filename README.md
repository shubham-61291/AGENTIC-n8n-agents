<div align="center">

# AGENTIC-n8n-agents

### A portfolio of AI-powered workflow automations built with n8n

**Email automation · HR workflows · Retrieval-augmented generation · MCP · Social research · Voice outreach · Generative storytelling**

[![n8n](https://img.shields.io/badge/automation-n8n-EA4B71?style=flat-square)](https://n8n.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](./LICENSE)
![Workflow exports](https://img.shields.io/badge/workflows-JSON-4B7BEC?style=flat-square)

</div>

---

## Overview

**AGENTIC-n8n-agents** is a curated collection of autonomous-agent and workflow projects built around [n8n](https://n8n.io/), large language models—including Google Gemini and OpenAI—and the **Model Context Protocol (MCP)**. The projects focus on practical use cases across sales outreach, recruitment, HR knowledge access, email handling, social-media analytics, and creative content generation. The story-generation workflow produces moral-based stories of approximately 1,200–1,500 words using Google Gemini.

The repository presents a collection of production-ready agents targeting real-world use cases and includes importable n8n workflow JSON exports with project-specific documentation. Each project README explains the workflow’s intended behavior, integrations, configuration steps, security considerations, and demonstration video.

> **Public-export note:** Workflow exports in this repository are sanitized for publication. Personal information, credential references, account-specific IDs, webhook values, and other sensitive details may be removed or replaced with placeholders. These are deliberate security measures. Configure the corresponding values for your own environment before importing or running a published export. Examples of configurable values include `YOUR_WEBHOOK_ID`, `YOUR_GEMINI_API_KEY`, and `YOUR_AIRTABLE_BASE_ID`. A redacted public export should not be taken as a description of the original configured demonstration environment.

## Project index

| Project | What it does | Main integrations | Workflow export / documentation | Demo |
|---|---|---|---|---|
| **Sales calling and meeting scheduling** | Reads lead details from Google Sheets and starts outbound calls through Retell AI; the configured Retell agent introduces the offering, captures requirements, and offers a meeting/demo. | n8n, Google Sheets, Retell AI | [`sales_calling_agent_n8n.json`](./sales-calling/sales_calling_agent_n8n.json) · [README](./sales-calling/README.md) | [Watch demo](https://www.youtube.com/watch?v=e_3sMgFad9E&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=3) |
| **Automatic email labelling and reply** | Classifies incoming Gmail messages as Sales, Promotion, or Other, applies labels, and drafts/sends a tailored reply for sales enquiries. | n8n, Gmail, Google Gemini | [`automatic_email_reading_label_&_reply.json`](./auto-email-labelling-reply/automatic_email_reading_label_&_reply.json) · [README](./auto-email-labelling-reply/README.md) | [Watch demo](https://www.youtube.com/watch?v=oTsM5ict2xc&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1) |
| **HR CV screening and rating** | Processes CV emails, extracts candidate details, evaluates fit against a job description, assigns a score out of 10, and records results in Google Sheets. | n8n, Gmail, AI model, Google Sheets | [`HR_AI_AGENT_CV_SCREENING.json`](./hr-cv-screening/HR_AI_AGENT_CV_SCREENING.json) · [README](./hr-cv-screening/README.md) | [Watch demo](https://www.youtube.com/watch?v=mOv1Xj8OaPE&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=2) |
| **Website-integrated HR RAG chatbot** | Answers employee questions with HR-policy context retrieved from Supabase, retains conversational context with Postgres, and includes a document-ingestion path. | n8n, Google Gemini, Supabase, Postgres | [`RAG_BASED_HR_CHATBOT_WEBSITE_INTEGRATED.json`](./RAG_HR_AGENT_WEBSITE_DEPLOYED/RAG_BASED_HR_CHATBOT_WEBSITE_INTEGRATED.json) · [README](./RAG_HR_AGENT_WEBSITE_DEPLOYED/README.md) | [Watch demo](https://www.youtube.com/watch?v=czIQ1PzZAg0&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=5) |
| **Instagram reel research** | Uses Apify to retrieve recent reels for creators listed in Airtable, sorts by play count, and stores each creator’s top five results. | n8n, Apify, Airtable | [`SOCIAL_MEDIA_SCRAPING_AGENT.json`](./SOCIAL_MEDIA_SCRAPING/SOCIAL_MEDIA_SCRAPING_AGENT.json) · [README](./SOCIAL_MEDIA_SCRAPING/README.md) | [Watch demo](https://www.youtube.com/watch?v=IiFAXrHNmjI&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=6) |
| **MCP server and workflow client** | Exposes Gmail message-sending as an MCP tool and demonstrates an AI-agent workflow invoking that tool through an MCP client. | n8n, MCP, OpenAI, Gmail | [`MCP_SERVER.json`](./MCP/MCP_SERVER.json) · [`MCP_WORKFLOW_CLIENT_TOOL.json`](./MCP/MCP_WORKFLOW_CLIENT_TOOL.json) · [README](./MCP/README.md) | [Watch demo](https://www.youtube.com/watch?v=21wv7vN3UvA&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=4) |
| **Telegram-powered email agent** | Connects a Telegram bot to a Gemini-powered agent with memory and Gmail tooling for natural-language email tasks and Telegram confirmations. | n8n, Telegram, Gmail, Google Gemini | [`telegram_connected_email_handling_agent.json`](./TELEGRAM_POWERED_EMAIL_AGENT/telegram_connected_email_handling_agent.json) · [README](./TELEGRAM_POWERED_EMAIL_AGENT/README.md) | [Watch demo](https://www.youtube.com/watch?v=cAWc6gxOVek&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=7) |
| **Web-based children’s story generator** | Accepts a topic through a webhook and generates a structured, moral-based story for children aged 5–10. | n8n, Google Gemini, HTTP webhook | [`WEBBASED_STORYGENERATOR_WITH_NARRATION.json`](./WEBHOSTED_STORYGENERATOR_&_NARRATION/WEBBASED_STORYGENERATOR_WITH_NARRATION.json) · [README](./WEBHOSTED_STORYGENERATOR_&_NARRATION/README.md) | [Watch demo](https://www.youtube.com/watch?v=-Qh1JDsCtR8&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=8) |

## Repository layout

```text
AGENTIC-n8n-agents/
├── MCP/
│   ├── MCP_SERVER.json
│   ├── MCP_WORKFLOW_CLIENT_TOOL.json
│   ├── README.md
│   └── LICENSE
├── RAG_HR_AGENT_WEBSITE_DEPLOYED/
│   ├── RAG_BASED_HR_CHATBOT_WEBSITE_INTEGRATED.json
│   ├── README.md
│   └── LICENSE
├── SOCIAL_MEDIA_SCRAPING/
│   ├── SOCIAL_MEDIA_SCRAPING_AGENT.json
│   ├── README.md
│   └── LICENSE
├── TELEGRAM_POWERED_EMAIL_AGENT/
│   ├── telegram_connected_email_handling_agent.json
│   ├── README.md
│   └── LICENSE
├── WEBHOSTED_STORYGENERATOR_&_NARRATION/
│   ├── WEBBASED_STORYGENERATOR_WITH_NARRATION.json
│   ├── README.md
│   └── LICENSE
├── auto-email-labelling-reply/
│   ├── automatic_email_reading_label_&_reply.json
│   ├── README.md
│   └── LICENSE
├── hr-cv-screening/
│   ├── HR_AI_AGENT_CV_SCREENING.json
│   ├── README.md
│   └── LICENSE
├── sales-calling/
│   ├── sales_calling_agent_n8n.json
│   ├── README.md
│   └── LICENSE
├── LICENSE
└── README.md
```

## Getting started

### 1. Choose a workflow

Open the project README from the index above, review the associated integrations and expected inputs, and select the matching JSON export. The MCP example uses **two workflow exports**, one for the server and one for the client.

### 2. Import into n8n

In n8n, open **Workflows → Import from File** and import the JSON export. For the MCP project, import both workflows.

### 3. Configure integrations and environment-specific values

Create or select the required credentials in n8n’s Credentials vault. Depending on the project, integrations include Gmail, Telegram, Airtable, Apify, Supabase, Postgres, OpenAI, Google Gemini, Google Sheets, and Retell AI. Restore your own webhook path/ID, API keys, account identifiers, table or sheet IDs, label IDs, caller ID, agent ID, and other required configuration where placeholders are present.

### 4. Test in your own environment

Follow the selected project’s setup and test procedure. Execute manually or connect the workflow to a website, chat app, or scheduling system as appropriate for its use case. Start manually when the workflow uses a manual trigger; for webhook-, Telegram-, Gmail-, or website-triggered projects, use the trigger and activation mode described in that project’s README. Confirm the expected result in the connected service.

## Security and publication hygiene

- Do not commit live API keys, OAuth secrets, bot tokens, webhook identifiers, private personal information, or account-specific configuration.
- Treat placeholders and removed values in the public exports as intentional redactions. Replace them with values belonging to your own environment before execution.
- Store secrets in n8n Credentials or environment variables rather than in publicly shared workflow files.
- Protect externally exposed webhooks and MCP endpoints using an appropriate gateway, access control, token, or IP allowlist.
- When handling email, candidate CVs, HR policies, or social-media data, use appropriate access permissions and follow the relevant platform policies.

## Why MCP is included

The repository also demonstrates the **Model Context Protocol (MCP)** as a way to separate tool hosting from tool use. This forward-looking pattern makes the workflows future-ready for extending agent capabilities through reusable tool integrations. A workflow can expose a capability such as sending Gmail messages, while a separate client or AI agent discovers and calls that tool. This separation offers a modular pattern for connecting agents to external systems—including email, calendars, databases, CRM, ERP, HR, and finance tools—without embedding each capability into every client workflow.

## Author

**Shubham Singh**

## License

This repository is distributed under the MIT License. See [`LICENSE`](./LICENSE). The full license text is also included below.

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
