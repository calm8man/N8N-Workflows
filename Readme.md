# N8N-Workflows

A collection of practical n8n automation workflows. Each workflow lives in its own folder with its own README, an exported workflow file, and an example environment file.

## Workflows

| Workflow | Description |
|---|---|
| [Ripple (XRP) Price Alert](./ripple) | Fetches the XRP price from CoinMarketCap and sends Telegram alerts on significant moves |
| [Ethereum Price Alert](./ethereum) | Same pattern applied to ETH |

## Repository structure

```
N8N-Workflows/
├── README.md
├── ripple/
│   ├── README.md
│   ├── workflow.json
│   └── .env.example
└── ethereum/
    ├── README.md
    ├── workflow.json
    └── .env.example
```

## Getting started

1. Clone the repository.
2. Open the folder of the workflow you want.
3. Read its README for requirements and setup.
4. Import `workflow.json` into n8n (Workflows > Import from File).
5. Copy `.env.example` to `.env` and add your own credentials.
6. Connect the credentials inside n8n and run the workflow.

## Tech used

- n8n
- REST APIs and JSON
- JavaScript (n8n Code node)
- Telegram integrations

## Security

- No API keys or tokens are stored in this repository.
- Every workflow ships with a `.env.example` that lists the required variables with placeholder values.
- Exported workflow files contain no credentials. Re-check before every commit.

## Contributing

This is a personal learning and portfolio repository. Issues and suggestions are welcome.
