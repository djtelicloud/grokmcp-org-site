# grokmcp-org-site

Static public lander for **grokmcp.org** (UniGrok), deployed via **ChatGPT Sites**.

This repo is **marketing and teaching content only**. It is intentionally boring.

## Policy

> **No secrets, no API keys, no live tool endpoints may ever be added to this repo or its deployment config.**

By policy this repo contains:

- **Zero secrets** — no keys, tokens, credentials, or `.env` files
- **Zero live tools** — no MCP endpoints, no callable tool surfaces
- **Zero server code** — static files only; nothing executes here

If a change needs any of the above, it belongs somewhere else (see below).

## File map

| Path | Purpose |
|---|---|
| `index.html` | Marketing landing page |
| `contribute/` | Contributor on-ramp page |
| `docs/` | Public teaching docs, incl. the OKF manifest (`docs/okf/okf-manifest.json`) |
| `.well-known/unigrok.json` | Machine discovery contract |
| `llms.txt` | LLM-readable site index |
| `api/public/v1/project` | Public project metadata (static JSON, extensionless file) |

## Where the real things live

- **Product / server code:** https://github.com/djtelicloud/grok-mcp-server
- **Contributor funnel:** https://control.grokmcp.org

See `DEPLOY.md` for the cutover checklist.
