<div align="center">

# Instagram Reel Research Agent

### Collect, rank, and store high-performing creator reels with n8n

[![n8n](https://img.shields.io/badge/automation-n8n-EA4B71?style=flat-square)](https://n8n.io/)
![Integrations](https://img.shields.io/badge/integrations-Apify%20%7C%20Airtable-4B7BEC?style=flat-square)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](./LICENSE)

</div>

## Overview

The Insta Scraper Agent automates Instagram reel research for a list of creators. It reads creator Instagram IDs from Airtable, requests recent posts through the Apify Instagram Scraper Actor, ranks the results by `videoPlayCount`, and stores the top five reels per creator in an Airtable table for tracking and analysis.

The workflow is started manually from n8n. A wait step adds a pause between creator requests to help avoid rate limiting.

## Workflow at a glance

| Stage | Behavior |
|---|---|
| **Manual trigger** | Starts when the operator clicks **Execute workflow**. |
| **Search records** | Retrieves creator rows from the Airtable creator list. |
| **Loop Over Items** | Processes creators one at a time. |
| **Wait** | Adds a delay between API calls, then cycles to the next creator. |
| **HTTP Request / Apify** | Calls the configured Apify Instagram Scraper Actor with the creator profile URL. The documented request fetches up to 20 posts from the last 15 days. |
| **Sort** | Orders the fetched reels by `videoPlayCount` in descending order. |
| **Limit** | Keeps the top five reels per creator. |
| **Create a record** | Writes selected reel details to Airtable’s “best performing reels” table. |

## Data written to Airtable

Each stored reel record is documented as containing:

- Creator name
- Reel URL
- Caption
- Date
- Views
- Likes
- Comments

The source creator list and destination performance table are separate Airtable tables: the first supplies Instagram creator IDs, and the second stores ranked reel details.

## Requirements

- n8n.
- An Airtable base with a creator-list table and a “best performing reels” table.
- Airtable credentials configured in n8n.
- An Apify account and API key, with access to the configured Instagram Scraper Actor.

## Setup

### 1. Import the workflow

Import [`SOCIAL_MEDIA_SCRAPING_AGENT.json`](./SOCIAL_MEDIA_SCRAPING_AGENT.json) using **Workflows → Import from File**.

### 2. Configure Airtable

Create or select Airtable credentials in n8n and bind them to both Airtable nodes. Confirm that the creator table contains the creator Instagram IDs expected by the workflow and that the destination table has fields for creator name, reel URL, caption, date, views, likes, and comments.

### 3. Configure Apify

Set up the Apify API key through n8n Credentials and bind it to the HTTP Request node. The actor URL in the export identifies the Apify Instagram-scraper endpoint; use the correct account-specific credential and configuration for your setup.

### 4. Restore environment-specific values

| Placeholder | Configure with |
|---|---|
| `YOUR_AIRTABLE_BASE_ID` | Your Airtable base ID. |
| `YOUR_AIRTABLE_TABLE_ID` | Your table IDs for the creator list and best-performing reels. |
| `YOUR_AIRTABLE_CREDENTIAL_ID` / `YOUR_AIRTABLE_CREDENTIAL_NAME` | Your Airtable credential reference in n8n. |
| `YOUR_APIFY_API_KEY` | Your Apify API key, stored securely. |
| `YOUR_WEBHOOK_ID` | The corresponding webhook value if used by your configured version. |

Some values may be intentionally sanitized in the repository’s public export. Configure your own values in n8n rather than adding private account information back into the public JSON.

### 5. Execute and verify

1. Add a test creator to the Airtable creator list.
2. Click **Execute workflow** in n8n.
3. Confirm that the recent posts are retrieved, sorted by view/play count, limited to five per creator, and written to the destination table with the expected fields.

## Operational considerations

- The workflow includes a wait node between API requests to reduce the likelihood of rate limiting.
- Respect Instagram’s terms and the applicable Apify actor limits and usage policies.
- Keep Airtable identifiers and API keys private.
- Use n8n Credentials or environment variables for secrets.

## Demonstration

[**Watch the Instagram reel-scraping demo**](https://www.youtube.com/watch?v=IiFAXrHNmjI&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=6)

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
