# Workflows Overview

Two workflows currently deployed on this n8n instance, tying together lab monitoring and notifications.

| Workflow file | Trigger | What it does | Why it exists |
|---|---|---|---|
| `service-health-check.json` | Schedule (every 15 min) | Pings a list of internal service URLs, and posts a message if any fail | Faster, more customizable signal than waiting on Uptime Kuma alone — lets me combine multiple checks into one notification instead of one alert per service |
| `door-sensor-alert.json` | Webhook (called from Home Assistant automation) | Receives a door-open event from Home Assistant, applies simple time-of-day logic (e.g. suppress during expected hours), and forwards to a notification channel | Keeps notification logic out of Home Assistant's own automation editor — easier to iterate on filtering rules in n8n's visual editor than in YAML |

Both are exported (sanitized — webhook URLs and any tokens replaced with placeholders) in `workflows/`.

## Sanitizing note

Before exporting any workflow from n8n: check every HTTP Request / Webhook node for hardcoded URLs, and every node's credentials — n8n stores credentials separately from the workflow JSON by default, but double-check before committing.
