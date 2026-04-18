# n8n-portfolio
# Hacker News → Discord Daily Digest

## What it does
Fetches the top Hacker News stories every morning at 08:00,
filters to only stories with score above 200 and a valid URL,
and posts a formatted digest to a Discord channel via webhook.

## Node stack
Schedule Trigger → HTTP Request (HN top IDs) → Code node (parse IDs)
→ Limit (20 items) → Split In Batches (loop) → HTTP Request (story detail)
→ IF (score > 200 AND url exists) → Wait (3s) → HTTP Request (Discord POST)

## Key concepts demonstrated
- Schedule-based triggering (daily at 08:00)
- Looping through API results with Split In Batches
- JavaScript in Code node to parse API response structure
- Conditional filtering with IF node
- Rate-limit handling with Wait node
- Webhook-based delivery to Discord

## APIs used
- Hacker News Firebase API (no auth required)
- Discord Incoming Webhook (free)

## Setup instructions
1. Create a Discord server and generate a webhook URL
   (Server Settings → Integrations → Webhooks → New Webhook)
2. In n8n: import workflow.json
3. In the HTTP Request2 node: paste your Discord webhook URL
4. Click Publish to activate the daily schedule

## Live Output 
<img width="1614" height="791" alt="image" src="https://github.com/user-attachments/assets/d4c5cd7e-e83a-4832-8dcb-10272bc1bd76" />

