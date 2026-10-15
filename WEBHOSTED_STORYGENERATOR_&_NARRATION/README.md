<div align="center">

# Web-Based Children’s Story Generator

### Topic-driven moral storytelling through an HTTP webhook

[![n8n](https://img.shields.io/badge/automation-n8n-EA4B71?style=flat-square)](https://n8n.io/)
[![Model](https://img.shields.io/badge/model-Google%20Gemini-4B7BEC?style=flat-square)](https://ai.google.dev/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](./LICENSE)

</div>

## Overview

This workflow generates long, moral-based stories for children aged **5–10** through a simple HTTP endpoint. A caller submits a topic in the `chatInput` field; Google Gemini generates a story through a Basic LLM Chain, and the Respond to Webhook node returns the story text to the requester.

The prompt is designed for stories of **1,200–1,500 words**—approximately **15+ minutes read aloud**—with an explicit moral lesson, engaging characters, a clear narrative arc, vivid and simple language, and no dark or scary themes.

## Story design requirements

| Dimension | Prompt requirements described in the project |
|---|---|
| **Audience** | Children aged 5–10. |
| **Length** | Approximately 1,200–1,500 words, targeting 15+ minutes when read aloud. |
| **Moral lesson** | A clear lesson such as kindness, honesty, or courage. |
| **Characters** | Relatable protagonists, including children, animals, or fantasy characters. |
| **Beginning** | Introduce the characters and setting. |
| **Middle** | Present a challenge or problem tied to the moral. |
| **End** | Resolve the problem and bring out the lesson learned. |
| **Style** | Simple, vivid language, repetition for engagement (for example, “And so it was…”), and dialogue that conveys emotion. |
| **Tone constraints** | Avoid dark or scary themes. |

## Workflow architecture

1. **Webhook** — accepts a `POST` request containing a topic in `chatInput`.
2. **Basic LLM Chain** — applies the story-generation prompt and organizes the requested story structure.
3. **Google Gemini Chat Model** — generates the story content.
4. **Respond to Webhook** — sends the generated story text back to the caller over HTTP.

This structure supports integration with a website, children’s educational app, chatbot, or another client that can issue an HTTP request and display the returned story.

## Example request

Send a `POST` request to your active webhook with a JSON body such as:

```json
{
  "chatInput": "Helping a lost puppy"
}
```

Another example topic is **“Sharing with Friends”**, in which a squirrel learns to share acorns and finds happiness.

The workflow’s documented result is a structured, moral-based story on the supplied theme, returned through the HTTP response.

## Requirements

- n8n with Webhook, Basic LLM Chain, Google Gemini Chat Model, and Respond to Webhook nodes.
- Google Gemini API access configured in n8n.
- A client or website capable of sending a JSON `POST` request to the webhook.

## Setup

### 1. Import the workflow

Import [`WEBBASED_STORYGENERATOR_WITH_NARRATION.json`](./WEBBASED_STORYGENERATOR_WITH_NARRATION.json) using **Workflows → Import from File**.

### 2. Configure Google Gemini

Add the Google Gemini (PaLM/Gemini API) credential in n8n and attach it to the chat-model node.

### 3. Configure the webhook

Set a webhook ID/path appropriate for your n8n environment, save the workflow, and use the generated URL for requests. The public export may use a placeholder for the webhook path or other environment-specific data.

| Placeholder | Purpose |
|---|---|
| `YOUR_WEBHOOK_ID` | Webhook identifier generated in your n8n instance. |
| `YOUR_WEBHOOK_PATH` | Path used by the webhook endpoint. |
| `YOUR_GEMINI_API_ID` / `YOUR_GEMINI_ACCOUNT` | Reference to the Gemini credential/account used by your environment. |

### 4. Run the workflow

Send a `POST` request containing a `chatInput` topic, such as `{"chatInput":"Helping a lost puppy"}`. Confirm that the webhook returns the generated story text.

## Use cases

- Story generation for children’s educational apps.
- A bedtime-story assistant triggered from a website or chatbot.
- A moral-storytelling companion for schools or parents.

## Security and deployment

- Do not publish live webhook IDs or Gemini credentials.
- Store secrets in n8n Credentials or environment variables.
- If the endpoint is exposed publicly, apply suitable access controls and request limits for your deployment.

## Demonstration

[**Watch the web-based story-generator demo**](https://www.youtube.com/watch?v=-Qh1JDsCtR8&list=PLlRRgrbOaGcaHAbVCTk70Nf0GerWXrqy1&index=8)

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
