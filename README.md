# AGENTIC-n8n-agents
Practical n8n workflows for building and deploying AI-powered agents.


AI Agentic Workflows (n8n + MCP + LLMs)

Purpose
This repository is a curated collection of autonomous agents and workflows built using n8n, large language models (Google Gemini, OpenAI), and emerging standards like Model Context Protocol (MCP). Each folder contains a production-ready agent focused on solving a real-world use case such as sales outreach, HR automation, email handling, social media analytics, or creative content generation.

Repository Structure

sales-calling-agent
Automates outbound calls using Retell AI, with contact details managed in Google Sheets.
DEMO VIDEO : - https://www.youtube.com/watch?v=e_3sMgFad9E&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=3

auto-email-labelling-reply-agent
Reads Gmail messages, labels them (Sales, Promotion, Other), and sends AI-powered replies.
DEMO VIDEO :- https://www.youtube.com/watch?v=oTsM5ict2xc&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1

hr-cv-screening-agent
Extracts CVs from Gmail, evaluates them against a Job Description, and rates candidates out of 10 in Google Sheets.
DEMO VIDEO :- https://www.youtube.com/watch?v=mOv1Xj8OaPE&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=2

hr-chatbot-website-integration
RAG-based chatbot that retrieves HR policies from Supabase vector store, remembers context via Postgres, and answers employee queries through a web interface.
DEMO VIDEO :- https://www.youtube.com/watch?v=czIQ1PzZAg0&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=5

insta-scraper-agent
Uses Apify to fetch Instagram reel data, sorts by play count, and stores top 5 reels per creator into Airtable.
DEMO VIDEO : - https://www.youtube.com/watch?v=IiFAXrHNmjI&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=6

mcpserver and mcpsimpleworkflow
Demonstrates MCP (Model Context Protocol). The server exposes Gmail send as a tool, and the client workflow calls it via AI Agent. Shows how MCP can separate tool hosting and tool usage.
DEMO VIDEO :- https://www.youtube.com/watch?v=21wv7vN3UvA&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=4

telegram-powered-email-handling-agent
Telegram bot connected with AI Agent to manage Gmail actions (compose, send, reply) using natural language.
DEMO VIDEO :- https://www.youtube.com/watch?v=cAWc6gxOVek&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=7

story-generator-agent
Webhook-triggered children’s story generator. Produces 1200–1500 word moral-based stories using Google Gemini.

Setup Instructions

Import the workflow JSON file from the desired agent folder into n8n.

Configure credentials in n8n Credentials vault (Gmail, Telegram, Airtable, Apify, Supabase, Postgres, OpenAI, or Google Gemini as required).

Replace placeholders like YOUR_WEBHOOK_ID, YOUR_GEMINI_API_KEY, YOUR_AIRTABLE_BASE_ID with your actual values.

Execute the workflow manually or connect it to a website, chat app, or scheduling system depending on the use case.

Security Notes

Do not commit real API keys, webhook IDs, or credentials.

All workflows in this repo are published with placeholders for safety.

Use n8n’s built-in Credentials vault or environment variables for sensitive information.

Importance of MCP
This repo also demonstrates workflows that implement the Model Context Protocol (MCP). MCP is becoming the backbone of autonomous agent ecosystems, enabling agents to dynamically discover and call external tools (email, calendar, CRM, ERP). By separating tool hosting (Server) and tool calling (Client), MCP allows enterprises to expose internal systems securely to AI agents. This forward-looking capability makes these workflows future-ready.

Author
Shubham Singh

License
MIT License
