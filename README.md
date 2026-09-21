# n8n — Workflow Automation

> Part of [homelab-hub](https://github.com/emaro03/homelab-hub). Self-hosted n8n instance used to automate tasks across the lab and beyond.

## Overview

n8n runs in Docker on the lab, orchestrating workflows that connect lab services (and external APIs) without needing to write and maintain a separate script/cron job for each one.

_Replace this with 2-3 real, specific workflows — this is the section recruiters actually read closely. Examples of the kind of detail that lands well:_
- "Workflow that watches for a new item in the *arr stack and posts a notification to \[wherever\]"
- "Workflow that runs a nightly health check across services and reports failures"
- Anything showing you use it for something beyond a demo.

## What's in this repo

| Path | Contents |
|---|---|
| `docker-compose.yml` | n8n service definition |
| `.env.example` | Required environment variables template |
| `workflows/` | Exported workflow JSONs (sanitized — remove any API keys/webhook URLs before exporting) |
| `docs/workflows-overview.md` | Plain-language explanation of what each exported workflow does and why |

## Sanitizing exported workflows

n8n workflow exports can contain credentials/URLs. Before committing an exported workflow JSON:
1. Open it and search for any API key, token, or internal hostname.
2. Replace with placeholders (`YOUR_API_KEY`, `internal-service.local`).
3. Double-check webhook URLs — these can leak your Cloudflare Tunnel hostname.

## Status / Known issues

_Note anything currently manual that you'd like to automate next — shows forward-thinking._

## License

MIT — see [LICENSE](LICENSE).
