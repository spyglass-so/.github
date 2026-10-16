<div align="center">
  <img src="https://raw.githubusercontent.com/spyglass-so/spyglass/main/assets/wordmark.svg" alt="Spyglass" width="360">

  <h3>The API layer for the social internet</h3>
  <p>Search brands, creators, and the ads they run. Then pull the creatives, hooks, landing pages, and comments behind them.</p>

  <a href="https://app.spyglass.so">
    <img src="https://img.shields.io/badge/Get_Started-7C3AED?style=for-the-badge" alt="Get Started">
  </a>
  <a href="https://docs.spyglass.so">
    <img src="https://img.shields.io/badge/Documentation-2563EB?style=for-the-badge" alt="Documentation">
  </a>
  <a href="https://github.com/spyglass-so/spyglass">
    <img src="https://img.shields.io/badge/SDK-0D9488?style=for-the-badge" alt="SDK">
  </a>
</div>

<br>

<div align="center">
  <a href="https://github.com/spyglass-so/spyglass/blob/main/LICENSE">
    <img src="https://img.shields.io/badge/license-MIT-0D9488" alt="License">
  </a>
  <a href="https://github.com/spyglass-so/spyglass/stargazers">
    <img src="https://img.shields.io/badge/Star_on_GitHub-F59E0B?logo=github&logoColor=white" alt="Star on GitHub">
  </a>
  <a href="https://spyglass.so">
    <img src="https://img.shields.io/badge/spyglass.so-DB2777" alt="spyglass.so">
  </a>
</div>

---

## Why Spyglass?

The social internet is where brands actually advertise. The creative, the hook, the landing page, and the comments live in different places, and none of them are built for a program to read.

Spyglass is one API for that layer. Resolve a brand or creator, then ask what they are running.

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

**[spyglass](https://github.com/spyglass-so/spyglass)** is the official client. TypeScript and Python, same resource names.

```bash
npm install @spyglass/sdk
```

```ts
import { Spyglass } from "@spyglass/sdk";

const spyglass = new Spyglass({ apiKey: process.env.SPYGLASS_API_KEY });

const { brands } = await spyglass.brands.search({ names: ["Nike"], limit: 1 });
const account = await spyglass.account.retrieve(brands[0].id);

for await (const ad of spyglass.media.list({ brandId: account.id, limit: 100 })) {
  console.log(ad.id, ad.title);
}
```

```bash
pip install spyglass-sdk
```

```python
from spyglass import Spyglass

spyglass = Spyglass()
brands = spyglass.brands.search(names=["Nike"], limit=1)
```

Keys are created in [Settings → API](https://app.spyglass.so). Full reference: [docs.spyglass.so](https://docs.spyglass.so).
