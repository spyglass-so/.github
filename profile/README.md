<div align="center">
  <img src="https://raw.githubusercontent.com/spyglass-so/spyglass-typescript/main/assets/wordmark.svg" alt="Spyglass" width="360">

  <h3>The API layer for the social internet</h3>
  <p>Search brands, creators, and the ads they run. Then pull the creatives, hooks, landing pages, and comments behind them.</p>

  <a href="https://app.spyglass.so">
    <img src="https://img.shields.io/badge/Get_Started-7C3AED?style=for-the-badge" alt="Get Started">
  </a>
  <a href="https://docs.spyglass.so">
    <img src="https://img.shields.io/badge/Documentation-2563EB?style=for-the-badge" alt="Documentation">
  </a>
  <a href="https://github.com/spyglass-so/spyglass-typescript">
    <img src="https://img.shields.io/badge/TypeScript_SDK-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript SDK">
  </a>
  <a href="https://github.com/spyglass-so/spyglass-python">
    <img src="https://img.shields.io/badge/Python_SDK-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python SDK">
  </a>
</div>

<br>

<div align="center">
  <a href="https://github.com/spyglass-so/spyglass-typescript/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/license-MIT-0D9488" alt="License">
  </a>
  <a href="https://github.com/spyglass-so/spyglass-typescript/stargazers">
    <img src="https://img.shields.io/badge/Star_on_GitHub-F59E0B?logo=github&logoColor=white" alt="Star on GitHub">
  </a>
  <a href="https://spyglass.so">
    <img src="https://img.shields.io/badge/spyglass.so-DB2777" alt="spyglass.so">
  </a>
</div>

<div align="center">
  <a href="https://x.com/spyglasshq">
    <img src="https://img.shields.io/badge/Follow_%40spyglasshq-white?style=social&logo=x&logoColor=black" alt="Follow @spyglasshq on X">
  </a>
</div>

---

## Why Spyglass?

The social internet is where brands actually advertise. The creative, the hook, the landing page, and the comments live in different places, and none of them are built for a program to read.

Spyglass is one API for that layer. Resolve a brand or creator, then ask what they are running.

## Our core ecosystem

### Official SDKs

<a href="https://github.com/spyglass-so/spyglass-typescript"><img align="right" src="https://img.shields.io/badge/SDKs-0D9488?style=for-the-badge" alt="SDK repositories"></a>

**[spyglass-so/spyglass-typescript](https://github.com/spyglass-so/spyglass-typescript)** & **[spyglass-so/spyglass-python](https://github.com/spyglass-so/spyglass-python)** — Official TypeScript (`@spyglass/sdk`) and Python (`spyglass-sdk`) clients.

Bring brand discovery, creator research, creatives, insights, landing pages, and comments into your own applications.

### Cloud API

<a href="https://docs.spyglass.so"><img align="right" src="https://img.shields.io/badge/Cloud_API-7C3AED?style=for-the-badge" alt="Cloud API documentation"></a>

**[Spyglass API](https://docs.spyglass.so)** — Social and creative intelligence over HTTP.

Get an API key, query the creative index, and return structured data to your product or research pipeline. Set a result limit to keep requests bounded.

[Get an API key](https://app.spyglass.so) · [Read the documentation](https://docs.spyglass.so)

### MCP server

<a href="https://app.spyglass.so/mcp"><img align="right" src="https://img.shields.io/badge/MCP_Server-2563EB?style=for-the-badge" alt="MCP setup"></a>

**[Connect Spyglass](https://app.spyglass.so/mcp)** — Bring creative research into your AI tools.

Connect an MCP client to Spyglass so your agent can research brands, creators, and creatives. Follow the setup guide in the app and sign in with your Spyglass account.

```text
https://app.spyglass.so/api/mcp
```

### API playground

<a href="https://app.spyglass.so/playground"><img align="right" src="https://img.shields.io/badge/Playground-DB2777?style=for-the-badge" alt="API playground"></a>

**[Try the playground](https://app.spyglass.so/playground)** — Explore requests before writing code.

Try brand, creator, and media queries from the app, inspect responses, and use the examples to start your integration. Sign in to get started.

## What you can ask for

| Call | What it answers |
| --- | --- |
| **Brands** | Which brand is this? Who else is in this space? |
| **Creators** | Which creator is this? Who matches this audience? |
| **Media** | What creatives is this account running, or what's out there for this theme? |
| **Insights** | Which hooks, personas, and formats does it lean on? |
| **Landing pages** | Where does its ad traffic go? |
| **Comments** | What are people saying on this post? |

Calls spend monthly credits, per row returned. Bound them with `limit`.

## Start with the SDK

Official clients for [TypeScript](https://github.com/spyglass-so/spyglass-typescript) and [Python](https://github.com/spyglass-so/spyglass-python).

```bash
npm install @spyglass/sdk
```

```ts
import { SpyglassClient } from "@spyglass/sdk";

const client = new SpyglassClient({ token: process.env.SPYGLASS_API_KEY! });

const { brands } = await client.search.searchBrandsV2({ names: ["Nike"], limit: 1 });
const brand = brands[0];

if (brand) {
  const { media } = await client.search.getMediaV2({ brandId: brand.id, limit: 20 });
  for (const ad of media) {
    console.log(ad.id, ad.hook);
  }
}
```

```bash
pip install spyglass-sdk
```

```python
import os
from spyglass import Spyglass

client = Spyglass(token=os.environ["SPYGLASS_API_KEY"])
result = client.search.search_brands_v2(names=["Nike"], limit=1)
```

Keys are created in [Settings → API](https://app.spyglass.so). Full reference: [docs.spyglass.so](https://docs.spyglass.so).

## What you can build

- **Competitor research:** resolve a brand, pull its creatives, and compare the hooks, formats, and landing pages behind its campaigns.
- **Creator discovery:** find creators for a niche, inspect their content, and build a shortlist for your next campaign.
- **Creative briefs:** combine media, account insights, and comments into a brief backed by source material.
- **Research agents and internal tools:** connect through the SDK, HTTP API, or MCP to bring social intelligence into your workflow.

## Who builds with Spyglass

- **Developers and AI agent builders** adding brand, creator, and creative research to their products.
- **Growth and creative teams** turning competitor activity into campaign ideas and briefs.
- **Agencies** researching clients' markets, discovering creators, and preparing pitches.

## Community & support

<p align="center">
  <a href="https://x.com/spyglasshq"><img src="https://img.shields.io/badge/Follow_%40spyglasshq-white?style=social&logo=x&logoColor=black" alt="Follow @spyglasshq on X"></a>
  <a href="https://github.com/spyglass-so/spyglass-typescript/issues"><img src="https://img.shields.io/badge/SDK_Issues-0D9488?style=for-the-badge&logo=github&logoColor=white" alt="Report an SDK issue"></a>
  <a href="https://docs.spyglass.so"><img src="https://img.shields.io/badge/Documentation-2563EB?style=for-the-badge" alt="Documentation"></a>
  <a href="mailto:support@spyglass.so"><img src="https://img.shields.io/badge/Email_Support-7C3AED?style=for-the-badge" alt="Email support"></a>
</p>

For SDK bugs and feature requests, open an issue in [`spyglass-typescript`](https://github.com/spyglass-so/spyglass-typescript/issues) or [`spyglass-python`](https://github.com/spyglass-so/spyglass-python/issues). For account, billing, or API questions, email [support@spyglass.so](mailto:support@spyglass.so).

---

<p align="center">
  <strong>The social internet, queryable.</strong><br>
  <a href="https://app.spyglass.so">Get your API key</a> and start building.<br><br>
  <a href="https://github.com/spyglass-so/spyglass-typescript">TypeScript SDK</a> · <a href="https://github.com/spyglass-so/spyglass-python">Python SDK</a> · <a href="https://app.spyglass.so/playground">Try the playground</a> · <a href="https://docs.spyglass.so">Read the docs</a>
</p>
