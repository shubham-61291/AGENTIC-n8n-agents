Auto Email Labelling & Reply Agent (n8n + Gmail + Gemini AI)

This agent automatically reads unread Gmail emails, classifies them into categories, applies Gmail labels, and sends an AI-generated reply for sales-related emails. It uses n8n for automation, Gmail API for reading and labelling, and Google Gemini (LLM) for classification and drafting replies.

Features

Reads unread emails from Gmail automatically.

Classifies emails into three categories:
• SALES – leads, quotes, orders, inquiries
• PROMOTION – offers, discounts, newsletters
• OTHER – support, personal, misc.

Applies Gmail labels dynamically for each category.

For SALES emails: generates a personalized AI reply including lead name, requirement, and a meeting scheduling link.

For PROMOTION and OTHER: only applies Gmail label, no reply.

Files

automatic_email_reading_label_&_reply.json → n8n workflow export.

Setup Instructions

Import Workflow

In n8n, go to Workflows → Import from File.

Upload automatic_email_reading_label_&_reply.json.

Gmail Setup

Replace placeholders with your own values:
• YOUR_SALES_LABEL_ID → Gmail label ID for sales emails
• YOUR_PROMOTION_LABEL_ID → Gmail label ID for promotions
• YOUR_OTHER_LABEL_ID → Gmail label ID for other emails

Retell/Gemini Setup

Replace YOUR_API_KEY with your Gemini API key.

Ensure the LLM node is connected and working.

Meeting Form Link

Replace YOUR_MEETING_FORM_LINK with your actual meeting scheduling link or form.

Webhooks

Replace YOUR_WEBHOOK_PLACEHOLDER with your actual n8n webhook ID or URL if needed.

Run Workflow

Start the workflow manually or set it to run periodically.

It will scan unread emails, classify, label them, and send replies where required.

Security

Do not commit your Gmail API credentials or Gemini API keys to GitHub.

Use environment variables inside n8n for sensitive information.

DEMO VIDEO :- https://www.youtube.com/watch?v=oTsM5ict2xc&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1

Next Steps

Extend the workflow to log responses into Google Sheets or CRM.

Add spam filtering for unwanted emails.

Enhance reply templates with more personalized messaging.

Author
Shubham Singh

License
MIT License
