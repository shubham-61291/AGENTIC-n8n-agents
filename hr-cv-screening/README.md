HR CV Screening & Rating Agent (n8n + Gmail + Google Sheets + AI)

This agent automates the process of reading candidate CVs from Gmail, extracting important details, evaluating them against a Job Description using AI, and recording the results with a rating out of 10 into a Google Sheet. It helps HR teams quickly shortlist candidates based on structured AI scoring.

Features

Reads unread CV emails from Gmail automatically.

Extracts candidate details such as first name, last name, email, phone, location, and skills.

Uses AI (Gemini or OpenAI) to evaluate the CV against the Job Description.

Assigns a rating score out of 10 for each candidate.

Appends candidate details and their rating into a Google Sheet.

Extensible for automating rejection or selection messages.

Files

hr_cv_screening_agent_n8n.json → n8n workflow export.

Setup Instructions

Import Workflow

In n8n, go to Workflows → Import from File.

Gmail Setup

Replace Gmail placeholders with your own credentials in n8n.

Ensure workflow can read unread emails with CV attachments.

Google Sheets Setup

Replace YOUR_SHEET_ID and YOUR_SHEET_URL with your Google Sheet details.

The sheet should have columns for: Name, Email, Phone, Location, Skills, Rating.

AI Model Setup

Replace YOUR_OPENAI_API_KEY or YOUR_GEMINI_API_KEY placeholders with actual keys.

Select the model node to evaluate CVs against JD.

Candidate Data Placeholders

Workflow uses placeholders like FIRST_NAME_PLACEHOLDER, LAST_NAME_PLACEHOLDER, EMAIL_PLACEHOLDER, PHONE_PLACEHOLDER, LOCATION_PLACEHOLDER.

These will be filled dynamically when CVs are processed.

Run Workflow

Trigger manually or schedule it.

Every unread email with a CV will be processed, scored out of 10, and appended to the Google Sheet.

Security

Do not commit real API keys, Gmail credentials, or sheet IDs.

Use environment variables inside n8n for sensitive values.

DEMO VIDEO :- https://www.youtube.com/watch?v=mOv1Xj8OaPE&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=2

Next Steps

Add thresholds (e.g., auto-flag candidates below 5/10).

Send automated rejection or interview emails.

Integrate with ATS/HRMS for end-to-end recruitment automation.

Author
Shubham Singh

License
MIT License
