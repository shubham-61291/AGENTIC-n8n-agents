<div align="center">

# HR CV Screening and Rating Agent

### Extract candidate details from Gmail CVs, evaluate fit, and record results in Sheets

[![n8n](https://img.shields.io/badge/automation-n8n-EA4B71?style=flat-square)](https://n8n.io/)
![Integrations](https://img.shields.io/badge/integrations-Gmail%20%7C%20Google%20Sheets-4B7BEC?style=flat-square)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](./LICENSE)

</div>

## Overview

The HR CV Screening Agent automates an initial candidate-review workflow. It reads unread CV emails from Gmail, extracts candidate information from attachments, evaluates each CV against a job description using an AI model, assigns a score out of 10, and records the structured result in Google Sheets.

The documented candidate fields are **first name, last name, email, phone, location, and skills**. The AI evaluation uses a job description (JD) as the comparison target. The README describes the model as Gemini or OpenAI, depending on the selected model configuration.

## Processing pipeline

| Stage | Purpose |
|---|---|
| **Gmail Trigger** | Detects unread email messages containing candidate CVs. |
| **Text Classifier** | Routes relevant CV emails for processing and sends non-matching items to a no-operation branch. |
| **Extract from File** | Extracts content from the CV attachment (the export includes PDF extraction). |
| **AI Agent** | Evaluates candidate fit against the job description and produces structured candidate details and a rating. |
| **AI model and Structured Output Parser** | Supports the agent’s model response and structured output. The setup documentation refers to Gemini or OpenAI as selectable options. |
| **Append or update row in sheet** | Writes candidate details and the rating into the configured Google Sheet. |

## Candidate output

The project documentation calls out these fields:

- Name (first and last)
- Email
- Phone
- Location
- Skills
- Rating (out of 10)

The destination Google Sheet should have corresponding columns. This workflow is intended to speed up initial review and provide structured scores for recruiter follow-up; the score should be considered an AI-generated screening aid rather than a replacement for human hiring decisions.

## Requirements

- n8n.
- Gmail access and a configured Gmail Trigger credential.
- CV attachments in the expected file format (the public export includes a PDF extraction path).
- A selected AI model credential, Gemini or OpenAI according to your configuration.
- Google Sheets credentials and a spreadsheet prepared with the candidate columns.
- A job description used by the evaluation instructions.

## Setup

### 1. Import the workflow

Import [`HR_AI_AGENT_CV_SCREENING.json`](./HR_AI_AGENT_CV_SCREENING.json) using **Workflows → Import from File**.

### 2. Configure Gmail

Connect your Gmail credential and ensure the workflow can read unread messages with CV attachments.

### 3. Configure Google Sheets

Set the spreadsheet ID and URL for your destination sheet and confirm the sheet includes columns for Name, Email, Phone, Location, Skills, and Rating.

### 4. Configure the AI evaluation

Provide your selected model credential (OpenAI or Google Gemini) and ensure the model node and structured output configuration match your chosen setup. Keep the job description used for the comparison current and role-specific.

### 5. Map candidate fields and placeholders

The source README names placeholders such as `FIRST_NAME_PLACEHOLDER`, `LAST_NAME_PLACEHOLDER`, `EMAIL_PLACEHOLDER`, `PHONE_PLACEHOLDER`, `LOCATION_PLACEHOLDER`, `YOUR_SHEET_ID`, `YOUR_SHEET_URL`, `YOUR_OPENAI_API_KEY`, and `YOUR_GEMINI_API_KEY`. Populate the corresponding mappings and credentials for your own deployment. The public export intentionally omits or replaces environment-specific and personal values; configure those locally rather than publishing private data.

### 6. Test the workflow

Trigger the workflow manually or schedule it as configured, using an unread test email containing a CV. Verify that candidate information is extracted, evaluated against the intended job description, scored out of 10, and written to the correct row in Google Sheets.

## Security and responsible use

- Keep Gmail credentials, AI API keys, and sheet identifiers private.
- Candidate CVs contain personal data. Restrict spreadsheet and mailbox access to authorized users.
- Review AI-generated scores and extracted data before making hiring decisions.
- Avoid logging or sharing candidate information beyond the authorized recruitment process.

## Possible extensions

- Add scoring thresholds (for example, flag candidates below 5/10).
- Send automated rejection or interview emails after human review or defined criteria.
- Integrate with an applicant-tracking system (ATS) or HRMS.

## Demonstration

[**Watch the HR CV screening demo**](https://www.youtube.com/watch?v=mOv1Xj8OaPE&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=2)

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
