Telegram Powered Email Handling Agent (n8n + Telegram + Gmail + Google Gemini)

Purpose
This agent connects a Telegram bot with Gmail to enable users to manage emails through conversational chat. It uses an AI Agent powered by Google Gemini to interpret user requests, maintain conversational memory, and trigger Gmail actions such as reading, composing, and sending emails. Responses and confirmations are sent back to the user over Telegram, making email management seamless within a chat interface.

Core Flow

Trigger: Telegram Trigger node listens for new chat messages.

AI Model: Google Gemini Chat Model processes the user’s Telegram input.

AI Agent: Interprets intent using a defined system prompt that enforces privacy, professionalism, and clarity. It decides when to call Gmail tools or reply directly.

Memory: Simple Memory node keeps track of conversation context for continuity.

Gmail Tool: Executes email operations (compose, send, reply) based on user instructions.

Telegram Response: Agent sends confirmations, summaries, or clarifications back to the user through Telegram.

What each node does

Telegram Trigger: Captures user input messages.

Google Gemini Chat Model: Provides AI reasoning and language understanding.

AI Agent: Orchestrates the workflow, ensuring Telegram-style responses for chat and professional tone for emails.

Simple Memory: Maintains context across sessions using Telegram user ID as session key.

Gmail Tool: Handles email operations like sending messages.

Send a text message: Returns AI Agent output to the user in Telegram.

Features

Bidirectional integration between Telegram and Gmail.

Natural language interface to process emails.

Context-aware responses via memory buffer.

AI-driven interpretation of ambiguous requests.

Privacy-conscious behavior with clear user confirmations.

Supports sending emails, replying to the latest message, or composing structured email content.

Setup Instructions

Import Workflow

In n8n, go to Workflows → Import from File and load the JSON file.

Configure Credentials

Telegram API: connect your Telegram bot.

Gmail OAuth2: authorize Gmail account for sending and replying.

Google Gemini (PaLM API): provide API key for the AI model.

Replace Placeholders (for public release)

YOUR_TELEGRAM_API_ID / NAME → actual Telegram bot credentials.

YOUR_GMAIL_CRED_ID / NAME → Gmail account credentials.

YOUR_GEMINI_API_ID / NAME → Google Gemini API credentials.

YOUR_WEBHOOK_ID → webhook IDs for each trigger node.

Run Workflow

Deploy Telegram bot.

Send a message like:
“Send an email to example@domain.com
 with subject ‘Meeting Update’ and message ‘Rescheduled to 4 PM.’”

The AI Agent will parse the request, trigger Gmail Tool, send the email, and confirm via Telegram.

Security Notes

Do not expose Telegram bot tokens, Gmail OAuth credentials, or API keys in public repositories.

Use n8n Credentials vault or environment variables for sensitive values.

Confirm all email actions before sending to avoid miscommunication.

Example Use Cases

Quick email replies from Telegram: “Reply to my last email with ‘Received, thank you.’”

Composing new messages: “Send email to manager@company.com
 with subject ‘Project Done’ and message ‘All tasks complete.’”

Notifications: Get confirmation on successful Gmail actions directly in chat.

Author
Shubham Singh

License
MIT License
