Insta Scraper Agent (n8n + Apify + Airtable)

Purpose
This agent automates Instagram reel scraping for a list of creators. It pulls creator handles from Airtable, scrapes their reels using Apify, sorts the content by performance, and writes the best-performing reels back into Airtable for tracking and analysis .

Core flow

Trigger: Manual start (“When clicking Execute workflow”).

Data source: Airtable table containing the list of creator Instagram IDs.

Loop: Iterates over each creator row.

API Call: Sends request to Apify Instagram Scraper Actor with creator profile URL, fetching up to 20 posts from the last 15 days.

Sorting: Sorts fetched reels by videoPlayCount in descending order.

Limit: Restricts results to top 5 reels per creator.

Storage: Creates new records in Airtable table “best performing reels” with fields: creator name, reel URL, caption, date, views, likes, comments .

Wait Node: Adds delay between API calls to avoid rate-limiting and cycles back for next creator .

What each node does

Search records: Queries Airtable base for creator list.

Loop Over Items: Iterates through each creator from the Airtable list.

Wait: Adds pause between API calls for stability.

HTTP Request: Calls Apify API to scrape Instagram posts for the current creator.

Sort: Orders scraped reels by play count.

Limit: Selects top 5.

Create a record: Inserts reel details into Airtable “best performing reels” table .

Setup (step by step)

Import the workflow

In n8n, go to Workflows → Import from File and load the JSON.

Connect credentials

Airtable: configure Airtable API token in n8n Credentials and link to both Airtable nodes.

Apify: configure Apify API key in n8n Credentials and bind it to the HTTP Request node .

Replace placeholders (for public version)

YOUR_AIRTABLE_BASE_ID → your Airtable base ID.

YOUR_AIRTABLE_TABLE_ID → your table IDs for “creator list” and “best performing reels”.

YOUR_AIRTABLE_CREDENTIAL_ID / NAME → your Airtable credential.

YOUR_APIFY_API_KEY → your Apify API key.

YOUR_WEBHOOK_ID → webhook node placeholder.

Execution

Run manually to trigger scraping.

Each creator’s recent reels will be scraped, top 5 selected, and results saved into Airtable.

Security notes

Do not expose Airtable Base IDs, Table IDs, or API keys in public repos.

Use environment variables or n8n Credentials to manage tokens.

Respect Instagram and Apify usage limits to avoid bans.

Testing

Add a test creator into Airtable “creator list”.

Execute workflow and confirm the top 5 reels are inserted into “best performing reels” table with correct details.

Author
Shubham Singh

License
MIT License
