# Proxy

Real-time Meta, Google, LinkedIn and TikTok ad library access via MCP. Free, no API keys.

## Components

- `mcp.json` — remote MCP server at `https://mcp.useproxy.dev/mcp?ref=cursor-plugin` (OAuth on first use)
- `skills/ad-research` — platform workflows, competitor discovery, creative analysis
- 12 playbook skills (`competitor-ad-teardown`, `ad-script-writing`, `winning-product-research`, `product-validation`, `digital-offer-research`, `who-is-advertising`, `brand-ad-audit`, `ad-swipe-file`, `landing-page-teardown`, `holiday-ad-campaigns`, `competitor-ad-watch`, `creative-brief-contact-sheet`) — each loads its method from Proxy with `get_playbook`. What each delivers: https://useproxy.dev/playbooks

## Install

- Cursor: Marketplace → Proxy → Install → Settings → Tools & MCP → connect `proxy`
- Grok Bot: Plugins → search "Proxy" → Add → Authorize

Docs: https://useproxy.dev/welcome
