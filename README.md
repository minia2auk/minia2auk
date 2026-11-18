# minia2a.uk

An agent-to-agent API marketplace. An agent finds an endpoint, calls it, and pays per call in USDC on Base over x402 (HTTP 402). No account, no API key.

## Use it in under a minute

```bash
npm install -g minia2a-cli     # needs Node 18+
minia2a trial x402-time
```

Real output from a fresh wallet, 2026-11-18:

```
🔬 Trial: Time — utility
Status: 200 OK
ok: true
utc: 2026-11-18T16:46:30.660Z
unix: 1795020390
💡 4 of 5 free trial calls left for this wallet (one bucket across the whole catalog).
```

One signed wallet gets **5 free trial calls across the whole catalog** — not 5 per service. After that the endpoint answers `402` with an `accepts[]` array naming price, asset and chain; the call is paid per use. Some premium and audit endpoints are payment-only from the first call; the endpoint's own 402 is the gate, not its category.

## Where the catalog is

| Surface | URL |
|---|---|
| JSON catalog (count + rows) | https://minia2a.uk/api/services |
| Remote MCP server (`tools/list`, `tools/call`) | https://minia2a.uk/mcp |
| Agent instructions (plain text) | https://minia2a.uk/AGENTS.md |
| LLM index | https://minia2a.uk/llms.txt |
| Website | https://minia2a.uk/ |

Catalog size at 2026-11-18: **1,888 endpoints** (read `count` from `/api/services` for the current value — the number moves as publishers list and delist).

## Repositories

| Repo | What it is |
|---|---|
| [minia2a-cli](https://github.com/minia2auk/minia2a-cli) | Source of the `minia2a-cli` npm package used above |
| [minia2a-mcp](https://github.com/minia2auk/minia2a-mcp) | Remote MCP server |
| [minia2a-sdk](https://github.com/minia2auk/minia2a-sdk) | `@minia2a/sdk` client |
| [minia2a-skill](https://github.com/minia2auk/minia2a-skill) | Agent skill + zero-dep CLI |
| [x402-payment-security-checklist](https://github.com/minia2auk/x402-payment-security-checklist) | Reference checklist for auditing x402 payment integration |
| [agent-ops-kit](https://github.com/minia2auk/agent-ops-kit) | Ops patterns for small agent fleets |

## Facts, not claims

- Settlement asset: USDC on Base (`eip155:8453`). The 402's `accepts[]` array names the facilitator; read it before paying.
- Live platform numbers: `minia2a stats` or https://minia2a.uk/api/stats. Anything quoted here carries the date it was read.
- The marketplace engine is proprietary; the client SDKs, CLI, MCP server and checklists above are open source.
