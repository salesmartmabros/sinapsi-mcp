# Sinapsi MCP — verified public wikis for your AI assistant

[![Sinapsi MCP connector](https://glama.ai/mcp/connectors/wiki.sinapsi/sinapsi/badges/score.svg)](https://glama.ai/mcp/connectors/wiki.sinapsi/sinapsi)

[Sinapsi](https://sinapsi.wiki/) serves curated, source-checked wikis over the [Model Context Protocol](https://modelcontextprotocol.io/). Your assistant (Claude, ChatGPT/Codex, Cursor, VS Code, …) searches them, cites the exact section it used, and sees what has **already been tried and did not work** — so it stops repeating dead ends.

- **Remote server, nothing to install.** Streamable HTTP, no API key needed for the public wikis.
- **11 public wikis, 1,063 pages**, each with declared provenance and a verification pass separate from the writing.
- **Negative knowledge on purpose:** "frontier" pages list theses already refuted, with the date and the fact that killed them.
- **Citations you can check:** every search result is a whole section with a stable `chunk_id`, linked to its page on the web.
- Listed in the official MCP Registry as `wiki.sinapsi/sinapsi`.

## Connect in one minute

All public wikis through one endpoint:

```
https://sinapsi.wiki/mcp/hub/
```

Or a single wiki: `https://sinapsi.wiki/mcp/w/<wiki-id>/` (see the table below).

**Claude Code**
```bash
claude mcp add --transport http sinapsi https://sinapsi.wiki/mcp/hub/
```

**Claude Desktop / claude.ai** — Settings → Connectors → *Add custom connector* → paste `https://sinapsi.wiki/mcp/hub/`

**Codex CLI**
```bash
codex mcp add sinapsi --url https://sinapsi.wiki/mcp/hub/
```

**Cursor** — `~/.cursor/mcp.json` ([example](examples/cursor-mcp.json))
```json
{ "mcpServers": { "sinapsi": { "url": "https://sinapsi.wiki/mcp/hub/" } } }
```

**VS Code** — `.vscode/mcp.json` ([example](examples/vscode-mcp.json))
```json
{ "servers": { "sinapsi": { "type": "http", "url": "https://sinapsi.wiki/mcp/hub/" } } }
```

Then ask something like: *"Using Sinapsi, what backtest traps make prediction-market strategies look profitable?"*

## Public wikis

| Wiki | Pages | Lang | What it covers | Single-wiki endpoint |
|---|---:|---|---|---|
| [Previsione geopolitica](https://sinapsi.wiki/w/previsione/) | 325 | it | Analisi geopolitica generata da una macchina con metodo dichiarato: fatti datati e verificati sulle fonti, posizioni degli analisti classificate e segnate contro gli esiti, tesi con la… | `https://sinapsi.wiki/mcp/w/previsione/` |
| [Open Problems and Verified Methods](https://sinapsi.wiki/w/ppt2/) | 275 | en | 275 pages of research mathematics: Erdős problems, the PPT² problem, the methods that worked and the routes already explored and closed. | `https://sinapsi.wiki/mcp/w/ppt2/` |
| [CTF Cryptography](https://sinapsi.wiki/w/ctf-crypto/) | 112 | en | 112 techniques for CTF crypto: given a signal, reach the right attack — with field-tested operational detail and a clear map of what does NOT work. | `https://sinapsi.wiki/mcp/w/ctf-crypto/` |
| [Prediction Markets, Measured](https://sinapsi.wiki/w/prediction-markets/) | 80 | en | 80 pages on how prediction markets actually behave, with Polymarket as the worked case: Bitcoin and other crypto Up/Down markets, weather, sports, esports and earthquakes. | `https://sinapsi.wiki/mcp/w/prediction-markets/` |
| [US Politics](https://sinapsi.wiki/w/us-politics/) | 57 | it | Reference-class base rates, polling methodology, institutional mechanics, and the 2026 races — the durable, source-verified knowledge for forecasting US elections and policy. | `https://sinapsi.wiki/mcp/w/us-politics/` |
| [Coding](https://sinapsi.wiki/w/coding/) | 56 | en | Field-tested lessons — the observable symptom, the real cause, the fix, and what didn't work — for the ways LLM-agent and web stacks fail, often silently. | `https://sinapsi.wiki/mcp/w/coding/` |
| [The Agent Economy](https://sinapsi.wiki/w/agent-economy/) | 51 | en | 51 pages on how AI agents pay and get paid, in two halves. | `https://sinapsi.wiki/mcp/w/agent-economy/` |
| [Google Ads](https://sinapsi.wiki/w/google-ads/) | 31 | en | 31 pages for marketers and their AI agents: auction mechanics, campaign setup, policy traps that get accounts suspended, and what does NOT work. | `https://sinapsi.wiki/mcp/w/google-ads/` |
| [Trading Edges](https://sinapsi.wiki/w/trading-edges/) | 28 | en | Market anomalies judged by evidence rather than by story. | `https://sinapsi.wiki/mcp/w/trading-edges/` |
| [GDPR Damages](https://sinapsi.wiki/w/gdpr-damages/) | 27 | en | 27 pages on compensation for data-protection breaches, built on 585 court decisions from 25 jurisdictions read in the official text and original language. | `https://sinapsi.wiki/mcp/w/gdpr-damages/` |
| [Model Context Protocol (MCP)](https://sinapsi.wiki/w/mcp/) | 21 | en | Connect any client and build a secure remote MCP server: transports, auth (Bearer/OAuth), the five primitives, and the failure modes that actually bite. | `https://sinapsi.wiki/mcp/w/mcp/` |

## Tools

| Tool | What it does |
|---|---|
| `list_wikis` | the wikis you can query, with size and description |
| `search` | returns whole sections (not snippets) with `chunk_id`, weight and provenance; pass `wiki="<id>"` to stay in one wiki |
| `get_page` | full page with its links, provenance and "what links here" |
| `neighbors` | pages linked to a page — follow the curated links similarity search misses |
| `stats` | size and verified-use counts of a wiki |
| `confirm_use` | tell the wiki which sections held up (`worked=true`) or were wrong (`worked=false` + correction) — this is how it improves for the next reader |

Signed-in users also get private spaces (team memory, EU-hosted): `my_spaces`, `write_page`, `my_documents`/`read_document` for uploaded PDF, Word, PowerPoint and Excel files, and `publish_space` to turn a space into a public wiki after an independent fact-check. See [sinapsi.wiki/for-developers](https://sinapsi.wiki/for-developers/) and [pricing](https://sinapsi.wiki/pricing/).

## How to cite

Search results carry a `chunk_id`; cite it as `[cit:chunk_id]` and link the page URL. Wiki content is licensed **CC BY 4.0** — attribute "Sinapsi (sinapsi.wiki)".

## About

Sinapsi is a product of **Salesmart S.r.l.** (Italy). Data in the EU. Privacy, terms and DPA: [sinapsi.wiki](https://sinapsi.wiki/).
Issues and suggestions are welcome in this repository.

The files in this repository (README, examples, `server.json`) are MIT-licensed; the wiki content served by the endpoints is CC BY 4.0.
