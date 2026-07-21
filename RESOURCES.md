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
| [twentyhq/twenty](https://github.com/twentyhq/twenty) | 45k | Modern open-source CRM with Kanban **deal pipelines** and custom objects. Backbone/reference for the Opportunity Timeline + Task Center. **AGPL-3.0** — fine for a private single-user app, but constrains reselling as hosted SaaS. |

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

## 7. AI browser workers — the free sourcing engine (Tier 2)

The modern replacement for hand-written Selenium scrapers. This is what lets "the app finds the deals" run on **free public county records** instead of paid lists.

| Repo | ★ | Why it matters |
|---|---|---|
| [browser-use/browser-use](https://github.com/browser-use/browser-use) | ~60k | AI agent that drives a real browser from a plain-English goal (~90% on WebVoyager). Best fit for the county-record workers; bring-your-own Claude. **Permissive license — safe even if we ever go SaaS.** Start here. |
| [Skyvern-AI/skyvern](https://github.com/skyvern-ai/skyvern) | 22k | LLM + computer-vision browser automation that handles CAPTCHAs / 2FA natively — for the tougher county sites. **AGPL-3.0** (private single-user use is fine). |
| [apify/crawlee](https://github.com/apify/crawlee) | ~16k | Playwright-based crawler framework for the scheduled nightly batch runs, retries, and anti-block handling. |

---

## 8. Free public data sources (keep the paid API a gap-filler)

Not repos, but the free feeds our workers and Land Intelligence read. Using these is what keeps the proposal's "no new running cost except data" claim honest.

| Source | What it gives | Why it matters |
|---|---|---|
| County assessor & GIS portals | Parcel, owner, tax, deed records | The free Tier-2 data the browser workers read; public by law |
| [OpenAddresses](https://openaddresses.io/) | Normalized US address data | Address backbone, free and open |
| [Census / ACS](https://data.census.gov/) + TIGER/Line | Demographics, home values, parcel/boundary geometry | Free enrichment plus map geometry |
| FEMA flood · HUD rents · FBI crime · Walk Score | Flood zones, market rents, safety scores | Free government APIs feeding Land Intelligence and scoring |
| [Redfin Data Center](https://www.redfin.com/news/data-center/) + [Zillow Research](https://www.zillow.com/research/data/) | Market-level comps and trends (CSV) | Free comps context — aggregate, not parcel-level |
| [Regrid](https://regrid.com/api) | Nationwide parcels + zoning | Not open-source, but a **free tier (~25 lookups/day)** for gap-fill |

---

## 9. Deal calculators / underwriting

| Repo | ★ | Why it matters |
|---|---|---|
| [berkcankapusuzoglu/Rental-Property-Deal-Analyzer](https://github.com/berkcankapusuzoglu/Rental-Property-Deal-Analyzer) | — | 20+ metrics, deal scoring, Cash Flow / BRRRR / Flip strategy fit. Closest match to our Calculators + Opportunity Score — lift the formulas. |
| [brarcher/rental-calc](https://github.com/brarcher/rental-calc) | — | Clean reference for closing costs, cash flow, and ROI math. |

---

## 10. Stack, UI & maps (boilerplate — skip weeks of setup)

| Repo | ★ | Why it matters |
|---|---|---|
| [KolbySisk/next-supabase-stripe-starter](https://github.com/KolbySisk/next-supabase-stripe-starter) | — | Next.js + Supabase + shadcn/ui + auth — our exact stack. Start here. Permissive license. |
| [ixartz/SaaS-Boilerplate](https://github.com/ixartz/SaaS-Boilerplate) | — | Next.js + Tailwind + shadcn + roles/permissions/i18n/testing. Alternative base. |
| [shadcn-ui/ui](https://github.com/shadcn-ui/ui) | — | Component library for the whole UI. |
| [maplibre/maplibre-gl-js](https://github.com/maplibre/maplibre-gl-js) | — | Free, open Mapbox alternative on OpenStreetMap for the Property and Land maps. |
| Nominatim / US Census Geocoder | — | Free geocoding (address ↔ lat/long), no per-call fee. |

---

## 11. Document reader (Phase 2)

| Repo | ★ | Why it matters |
|---|---|---|
| [jsvine/pdfplumber](https://github.com/jsvine/pdfplumber) | — | Extract text/tables from deeds, tax bills, and probate filings; pair with Claude for structured extraction into the deal record. |
| [pymupdf/PyMuPDF](https://github.com/pymupdf/PyMuPDF) | — | Fast PDF parsing/rendering for the same job. |

---

## Recommended plan of attack

1. **Clone and study `ai-realestate-claude`** — it's the closest working analog and Claude-native; borrow its analysis/skill structure.
2. **Scaffold on `next-supabase-stripe-starter`** — our exact stack (Next.js + Supabase + shadcn/ui), auth already wired; skips weeks of setup.
3. **Build the county workers on `browser-use`** (fall back to `skyvern` for hard sites) instead of hand-written Selenium — free public records only.
4. **Wire free data first** (Census/ACS, TIGER, FEMA flood, OpenAddresses, Redfin/Zillow CSVs); keep `batchdata-mcp-real-estate` / Regrid free tier as the paid gap-filler (Tier 1).
5. **Model the nightly agent on `fredy`** — schedule → match → alert.
6. **Lift calculator formulas from `Rental-Property-Deal-Analyzer`** for the Calculators + Opportunity Score.
7. **Borrow CRM/pipeline modeling from `RealEstateCRM` / `twenty`** for Contact Map, Opportunity Timeline, and Task Center.

> Licenses vary (MIT / GPL / AGPL / none). Confirm each before copying code, and never point scrapers at sites whose terms forbid it — county public records only.
>
> **License heads-up:** `Skyvern` and `twenty` are **AGPL-3.0** — perfectly fine for a private, single-user app you own, but avoid baking them into the codebase if Real Estate Dad ever ships as hosted SaaS. `browser-use`, the Supabase starter kits, `maplibre`, and `pdfplumber` are permissive, so lean on those if SaaS is ever on the table.
