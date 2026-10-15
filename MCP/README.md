MCP Server and Simple Workflow Agents (n8n + MCP + OpenAI + Gmail)

Purpose
This setup demonstrates the use of the Model Context Protocol (MCP) in n8n for connecting agents, tools, and workflows seamlessly. It consists of two parts:

MCP Server – exposes a tool (Gmail send message) via a webhook.

Simple Workflow – uses an AI agent with OpenAI, takes form input from a user, and calls the MCP Client to trigger the Gmail send message tool from the MCP Server. Together, they show how autonomous workflows can use MCP as a bridge between local logic and external tools. 

MCP Server Flow

Trigger: MCP Server Trigger node starts when a tool call is made.

Tool: Gmail Tool node configured to send an email message with fields (To, Subject, Message) filled dynamically.

Connection: The MCP Server Trigger exposes this Gmail action as a callable tool for any MCP Client. 

Simple Workflow Flow

Trigger: Form submission with fields: Name, Email, Issue, Preferred Date, Preferred Time.

AI Model: OpenAI Chat Model parses the form submission and prepares structured JSON.

AI Agent: Uses a system prompt that ensures a Gmail send tool call is always created. The email includes an acknowledgement message with the user’s issue, and confirms that the AI agent will call on the preferred date and time.

MCP Client: Connects to the MCP Server endpoint, exposing the Gmail tool. The AI Agent invokes this MCP Client to actually send the acknowledgement email.

End Result: User submits a form → AI Agent processes → MCP Client calls MCP Server → Gmail sends acknowledgement. 

Features

Demonstrates MCP Server exposing Gmail as a reusable tool.

Shows how an MCP Client workflow can call that tool on demand.

Structured form → AI Agent → Gmail pipeline for automated acknowledgements.

Clean separation between tool hosting (Server) and tool calling (Client).

Extensible to add more tools (e.g., calendar scheduling, CRM updates) exposed via MCP.

Setup Instructions

Import both workflows into n8n: mcpserver.json and mcpsimpleworkflow.json.

Configure credentials:

Gmail OAuth for the Gmail Tool.

OpenAI API key for the AI Model.

Replace placeholders:

YOUR_WEBHOOK_ID → actual webhook ID from your n8n instance.

YOUR_MCP_ENDPOINT_URL → the endpoint URL for the MCP Server.

YOUR_GMAIL_CRED_ID / NAME → Gmail credentials.

YOUR_OPENAI_API_ID / NAME → OpenAI credentials.

Publish the MCP Server workflow to expose the Gmail tool.

Connect the Simple Workflow MCP Client to the Server endpoint.

Test by submitting the form; confirm that the acknowledgement email is sent through Gmail.

Security Notes

Do not expose real webhook IDs or API keys in public repositories.

Keep Gmail and OpenAI credentials in n8n Credentials vault.

The MCP endpoint should be protected if exposed beyond your environment.

DEMO VIDEO :- https://www.youtube.com/watch?v=21wv7vN3UvA&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=4

Importance of MCP in Autonomous Agents
The Model Context Protocol (MCP) is rapidly becoming a backbone for connecting agents with external tools in a secure, standardized way. Instead of hardwiring API calls inside every workflow, MCP allows tools like Gmail, Calendars, Databases, and Custom APIs to be exposed as reusable capabilities. Autonomous agents can then dynamically discover and invoke these tools as needed.

This separation of “tool hosting” and “tool calling” makes agent systems more modular, scalable, and easier to govern. For enterprises, MCP will allow safe exposure of business-critical systems (ERP, CRM, HR, Finance) to AI agents without rewriting connectors for each one. Going forward, MCP adoption will be central to building reliable, production-grade autonomous agents.

Author
Shubham Singh

License
MIT License



## Repository workflow files

- [`MCP_SERVER.json`](./MCP_SERVER.json) — MCP server workflow export.
- [`MCP_WORKFLOW_CLIENT_TOOL.json`](./MCP_WORKFLOW_CLIENT_TOOL.json) — MCP client workflow export.

## Public-export and security context

The workflow JSON is a sanitized public export. Replace intentionally removed account-specific values and configure Gmail OAuth, OpenAI credentials, webhook ID, and MCP endpoint URL in your own n8n instance. Keep the MCP endpoint protected if exposed beyond your environment. These setup requirements are not a claim that the original demonstration was non-functional.

## License

This project is licensed under the MIT License. See [`LICENSE`](./LICENSE) for the standalone license file.

### MIT License Text

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
