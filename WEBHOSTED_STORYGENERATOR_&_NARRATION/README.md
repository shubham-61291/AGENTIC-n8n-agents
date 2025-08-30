Web-based Children’s Story Generator (n8n + Google Gemini)

Purpose
This agent generates long, moral-based children’s stories through a simple web endpoint. It is designed for ages 5–10, producing vivid and engaging stories of 1,200–1,500 words that take about 15+ minutes to read aloud. Each story embeds a clear moral lesson (e.g., kindness, honesty, courage) and avoids dark or scary themes. The agent uses Google Gemini as the language model and can be triggered via an HTTP webhook.

Core Flow

Trigger: Webhook node receives POST requests with a chatInput value (topic).

LLM: Google Gemini Chat Model processes the input.

Chain: Basic LLM Chain node applies a system-defined storytelling template to ensure structure and moral consistency.

Response: Respond to Webhook node sends the generated story back to the requester.

Story Requirements (as enforced in the workflow prompt)

Length: 1,200–1,500 words (~15+ minutes read aloud).

Moral: Embeds a clear lesson (kindness, honesty, courage, etc.).

Characters: Relatable (kids, animals, or fantasy beings).

Plot Structure:

Beginning: introduce characters and setting.

Middle: introduce a challenge tied to the moral.

End: resolve the problem and present the lesson.

Style: vivid language, repetition for engagement, dialogue to convey emotions.

Avoid: scary or dark themes.

Example topic: “Sharing with Friends” → A squirrel learns to share acorns and finds happiness.

Features

Generates complete structured children’s stories from simple prompts.

Built-in template enforces moral storytelling style.

Simple webhook trigger for integration with websites or apps.

Automatic HTTP response with full story text.

Setup Instructions

Import Workflow

In n8n, go to Workflows → Import from File and load the JSON.

Configure Credentials

Google Gemini (PaLM API) → connect via n8n Credentials.

Replace Placeholders (for public release)

YOUR_WEBHOOK_ID → webhook ID.

YOUR_WEBHOOK_PATH → webhook path.

YOUR_GEMINI_API_ID / YOUR_GEMINI_ACCOUNT → Gemini API credentials.

Run Workflow

Send a POST request to the webhook URL with a chatInput topic, e.g.:
{ "chatInput": "Helping a lost puppy" }

The workflow will generate a structured, moral-based story on the given theme.

Security Notes

Do not expose real webhook IDs or Gemini credentials in public repositories.

Use environment variables or the n8n Credentials vault for sensitive values.

Example Use Cases

Story generator for kids’ educational apps.

Bedtime story assistant triggered from a website or chatbot.

Moral storytelling companion for schools or parents.

Author
Shubham Singh

License
MIT License
