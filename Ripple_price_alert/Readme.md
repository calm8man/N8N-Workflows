# Ripple (XRP) Price Alert

An n8n workflow that checks the current XRP price on a schedule, calculates how much it moved, and sends an alert to Telegram when the move crosses a threshold.

## How it works

1. **Schedule Trigger** starts the workflow at a fixed interval.
2. **HTTP Request** calls the CoinMarketCap quotes API for XRP (authenticated with an API key header).
3. **Code node (JavaScript)** extracts the price and the percentage change from the nested JSON response and decides whether an alert is needed.
4. **IF node** lets the flow continue only when the threshold condition is met.
5. **Telegram** nodes send the alert message.

## Skills demonstrated

- REST API calls with header-based authentication
- Parsing nested JSON responses
- Minimal JavaScript in the n8n Code node
- Conditional branching
- Notification delivery through Telegram
- Keeping secrets out of the repository (`.env.example`)

## Requirements

- n8n (cloud or self-hosted)
- A CoinMarketCap API key
- A Telegram bot token and chat ID

## Setup

1. Import `workflow.json` into n8n (Workflows > Import from File).
2. Copy `.env.example` to `.env` and fill in your own values. Never commit real keys.
3. Create the credentials in n8n (Telegram) and select them in the matching nodes.
4. Set your API key in the HTTP Request node header (`X-CMC_PRO_API_KEY`), or reference it through an environment variable.
5. Adjust the alert threshold in the Code node.
6. Run the workflow manually once to test, then activate it.

## Configuration

| Variable | Description |
|---|---|
| `CMC_API_KEY` | CoinMarketCap API key |
| `TELEGRAM_CHAT_ID` | Chat that receives alerts |
| `ALERT_THRESHOLD_PERCENT` | Minimum price change that triggers an alert |

## Example alert

```
XRP price alert
Price: $0.52
Change (24h): +4.8%
```

## Notes

- The free CoinMarketCap plan has a monthly request limit, so do not set the schedule too aggressively.
- This workflow sends alerts only. It does not trade or give financial advice.
