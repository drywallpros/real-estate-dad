# Open-Source Building Blocks

GitHub projects that can accelerate Real Estate Dad, grouped by what they help with. Star counts and notes as of July 2026. **Always check each repo's LICENSE before reusing code, and respect site terms before scraping.**

---

## 1. Closest concept matches — study these first

| Repo | ★ | Why it matters |
|---|---|---|
| [zubair-trabzada/ai-realestate-claude](https://github.com/zubair-trabzada/ai-realestate-claude) | 126 | **The nearest thing to what we're building.** An AI real estate research engine *for Claude Code* — comps, rental income, neighborhood, investment potential, residential/commercial/flip/BRRRR analysis + PDF reports. 15 skills, 5 agents. Claude-native, matches our stack. Best reference for how to structure the AI analysis + skills. |
| [miron-tech/wholesaler-claude-skills](https://github.com/miron-tech/wholesaler-claude-skills) | 38 | 6 Claude Code skills for wholesalers — property recon, comp analysis, creative finance, deal stacking, CRM integration, powered by MCP servers. Directly maps to our Deal Analysis, Contact Map, and outreach features. |
| [AleksNeStu/ai-real-estate-assistant](https://github.com/AleksNeStu/ai-real-estate-assistant) | 282 | AI real estate platform: **Next.js + FastAPI + ChromaDB (RAG)**, conversational property search, Mapbox, mortgage calc. Great architecture reference — the Next.js frontend matches our stack. |

---

## 2. Data sourcing (Tier 1 API + Tier 2 scraping)

| Repo | ★ | Why it matters |
|---|---|---|
| [zellerhaus/batchdata-mcp-real-estate](https://github.com/zellerhaus/batchdata-mcp-real-estate) | 31 | **MCP server for BatchData.io** property + address APIs, TypeScript, built for Claude. This is essentially our Tier 1 `ApiAdapter` pre-built — owner data, skip-trace, distress flags exposed to the AI. Strong starting point. |
| [ZacharyHampton/HomeHarvest](https://github.com/ZacharyHampton/HomeHarvest) | 714 | Python package that scrapes property data (Zillow, Redfin, Realtor). Actively maintained. ⚠️ **ToS caution** — these sites restrict scraping; use for prototyping/comps, not as the production backbone. |
| [akashsakhiya07/jackson-county-tax-delinquent-scraper](https://github.com/akashsakhiya07/jackson-county-tax-delinquent-scraper) | 0 | Small, new, but exactly the **pattern** for our county browser workers: Selenium scraper pulling delinquent property tax records from a public court site (owner, tax amount, map link). Copy the technique, not the county. |
| [cporter202/API-mega-list](https://github.com/cporter202/API-mega-list) | 7.3k | Huge API directory including real-estate + web-scraping sources. Use to shop for cheaper/alternative data APIs. |

---

## 3. Autonomous search + alerts (Phase 2 nightly agent)

| Repo | ★ | Why it matters |
|---|---|---|
| [orangecoding/fredy](https://github.com/orangecoding/fredy) | 1.3k | "**F**ind **R**eal **E**state **D**amn Eas**y**" — continuously searches property portals and pushes matches to Slack/Telegram/Email/Discord. Germany-focused, but it's the **blueprint for our autonomous nightly agent**: scheduled search → filter against criteria → multi-channel alerts. |

---

## 4. CRM / pipeline / contact map

| Repo | ★ | Why it matters |
|---|---|---|
| [prolinkinfo/RealEstateCRM](https://github.com/prolinkinfo/RealEstateCRM) | 331 | Full real-estate CRM (MERN). Reference for our Contact Map, pipeline stages, and Task Center — how to model contacts, deals, and follow-ups. |
| [microrealestate/microrealestate](https://github.com/microrealestate/microrealestate) | 1.1k | Mature open-source property/rental management. More landlord-ops than investing, but solid patterns for the Portfolio module. |

---

## 5. Land / zoning intelligence

| Repo | ★ | Why it matters |
|---|---|---|
| [AlpacaLabsLLC/skills-for-architects](https://github.com/AlpacaLabsLLC/skills-for-architects) | 252 | Claude Code skills for architecture, **real estate, and zoning / space planning**. Reference for our Land Intelligence and development-feasibility features, in the same skills format. |

---

## 6. MCP-building references

| Repo | ★ | Why it matters |
|---|---|---|
| [tae0y/real-estate-mcp](https://github.com/tae0y/real-estate-mcp) | 360 | Real-estate MCP server over a government open API (Korea). Clean **pattern** for wrapping a property-data source as an MCP tool Claude can call. |
| [awesome-real-estate](https://github.com/etewiah/awesome-real-estate) | 348 | Curated list of real-estate dev resources and projects — mine it for more building blocks. |

---

## Recommended plan of attack

1. **Clone and study `ai-realestate-claude`** — it's the closest working analog and Claude-native; borrow its analysis/skill structure.
2. **Use `batchdata-mcp-real-estate`** as the starting point for the paid data adapter (Tier 1) instead of writing one from scratch.
3. **Copy the `jackson-county` scraper pattern** for the first county browser worker (Tier 2), per county.
4. **Model the nightly agent on `fredy`** — schedule → match → alert.
5. **Borrow CRM/pipeline modeling from `RealEstateCRM`** for Contact Map + Task Center.

> Licenses vary (MIT / GPL / none). Confirm each before copying code, and never point scrapers at sites whose terms forbid it — county public records only.
