# Build Prompt — Real Estate Dad

Copy everything below the line into an AI coding agent (Claude Code, Cursor, etc.) to scaffold and build the MVP. Pair it with `PROJECT_BRIEF.md` in the same folder.

---

## ROLE

You are a senior full-stack engineer building **Real Estate Dad**, a custom, **single-user** AI real estate investing app. Read `PROJECT_BRIEF.md` in full before writing code. Build the MVP defined in Section 10 of that brief.

## NON-NEGOTIABLE CONSTRAINTS

1. **Single user.** One account, one wealth plan, one pipeline. Do NOT build multi-tenancy, orgs, teams, or billing/subscription plumbing.
2. **The app finds the deals — the client does almost nothing.** No CSV import, no manual list-pulling by the user. Sourcing is automated (see Data section).
3. **Never fabricate data.** Every stored field carries `source` and `retrieved_at`. The UI must visibly separate: Verified facts · AI analysis · User assumptions · Calculated estimates.
   - **ARV/comps rule:** the AI must NOT invent comparable sales or numbers. Pull real nearby sales from a data source, compute ARV with deterministic math, and let the AI only *explain* the estimate and flag its assumptions.
4. **Paid API calls are gated.** The app must never spend money silently. When only the paid API can answer, the AI Coach asks the user to confirm before fetching. Support an optional monthly spend cap.
5. **Isolated project.** This lives in its own folder/repo. It shares nothing with any other codebase.

## STACK

- Next.js (App Router) + React + TypeScript + Tailwind CSS
- Supabase (Postgres + Auth + Storage)
- Claude (Anthropic) as the AI coach/analysis model. Put all AI calls behind one `AiCoach` service.
- Playwright + Chromium for AI browser workers
- Google Maps or Mapbox for maps
- Deploy target: Vercel

## ARCHITECTURE — build these seams first

### 1. `PropertyDataService` (the core abstraction)
One service, pluggable adapters, single `getProperty(query)` entry point that runs a waterfall:

```
cache (Supabase) → free county/browser data → paid API (gap-fill only, gated)
```

Adapters:
- `CountyBrowserAdapter` — Playwright workers that read FREE PUBLIC county records (tax-sale lists, probate dockets, foreclosure notices, code violations). One config per target county. Start with 1–3 counties. Schedulable (nightly batch).
- `ApiAdapter` — the licensed vendor (property details, value/rent estimates, owner skip-trace). Pay-per-use. Every call gated + logged with cost.
- Leave a clean extension point for future adapters (e.g. Regrid parcels).

**Do NOT point browser workers at Zillow, Realtor.com, MLS, or any site whose terms forbid scraping.** County public records only.

### 2. Provenance on every field
Postgres columns / JSON shape must include `source` (`county` | `browser` | `api` | `ai_estimate` | `user_assumption`) and `retrieved_at` per data point. This drives both the waterfall and the "never fabricate" UI.

### 3. `AiCoach` service
Wraps Claude. Given a property + its provenance, returns: opportunity scores, deal analysis, action plan, and page-level coaching. System prompt personality: **teacher first, investor second, dad always — never hype, never pressure, always explain, always cite where numbers came from.**

## BUILD ORDER (MVP)

1. Project scaffold, Tailwind, Supabase client, auth (single user), env config.
2. Postgres schema: `properties` (with provenance), `wealth_plan`, `buy_box`, `opportunities`, `tasks`, `contacts`, `alerts`, `saved_searches`, `api_spend_log`.
3. `PropertyDataService` + `ApiAdapter` (stub the real vendor behind an interface so it runs before a key exists) + cache.
4. `CountyBrowserAdapter` for ONE target county as a proof of concept.
5. Wealth Planner (form → gaps → strategy → roadmap).
6. Buy Box generator (from wealth plan + strategy).
7. Property Search + Property Detail page (pulls via `PropertyDataService`).
8. `AiCoach`: opportunity scoring → deal analysis → action plan → per-page coaching.
9. Contact Map, Task Center, Alerts, Saved Searches.
9a. **Opportunity Timeline** — every property gets a living, append-only history (discovered → analyzed → owner identified → verified → contacted → offer → negotiating → purchased → portfolio), storing documents, contacts, and notes at each step. This is the "institutional memory" differentiator — make it a first-class model, not an afterthought.
10. Dashboard (today's opportunities, deals needing attention, deadlines, tasks, pipeline, wealth progress, portfolio, next actions).
11. Calculators (Rental, BRRRR, Flip, Wholesale, Cash Flow, ROI, Cap Rate, NOI, Development, Max Offer, Rehab Budget).

## COST GUARDRAILS (implement, don't just document)

- Log every paid API call with an estimated cost to `api_spend_log`.
- Before any paid call, check the monthly cap; if exceeded, ask the user instead of calling.
- Cache by data type with sane TTLs: parcel/geometry ≈ never, ownership ≈ quarterly, distress flags ≈ weekly, price/AVM ≈ monthly. Never re-pay for fresh-enough data.

## DEFINITION OF DONE (MVP)

- User creates a Wealth Plan in < 5 min.
- App auto-surfaces opportunities from at least one county (browser worker) with zero manual list work.
- Every opportunity shows scores, analysis, and a complete action plan, with visible provenance on each number.
- User can go from discovery → outreach without leaving the app.
- No paid call ever fires without either being under-cap or user-confirmed.
- `npm run build` and `npm run typecheck` are clean.

## DELIVER

Working Next.js app in its own folder, a `README.md` with setup + required env vars, and a short note on which county adapters are wired and how to add the next one.
