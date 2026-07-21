# Real Estate Dad — Project Brief

**Version:** 2.1
**Type:** Custom, single-user application (built for one investor)
**Status:** Scoping / pre-build
**Location:** Standalone app. Lives in its own folder or its own repo — never mixed into any other project.

---

## 1. Product Overview

Real Estate Dad is an AI-powered real estate investing platform that **teaches users how to build wealth through real estate** instead of simply showing property listings.

Unlike PropStream, BatchLeads, or DealMachine, Real Estate Dad explains *why* an opportunity exists, *what strategy* fits it, *who* the user should contact, and *what actions* move them closer to their financial goals.

The platform acts as an experienced investing mentor — not a chatbot.

### Mission

Help everyday investors think like professionals by combining public property data, AI coaching, calculators, and action plans into one system.

Every opportunity should answer:

- Why was it flagged?
- Is it worth pursuing?
- What strategy fits?
- What should I do next?
- Who should I contact?
- Does this move me toward my wealth goal?

---

## 2. Target User

This is a **custom app built for a single investor**. It is not a multi-tenant SaaS. There is one account, one wealth plan, one pipeline. Every design decision favors low cost and low effort for that one user over scale.

The user profile spans these investing styles (the app should support all of them):

- **Beginner** — needs guidance and education; doesn't know what to buy.
- **Experienced** — needs better deal flow, automation, opportunity tracking.
- **Land investor** — needs parcel intelligence, development potential, subdivision analysis.
- **Wholesaler** — needs motivated sellers, fast analysis, outreach planning.
- **Buy & hold** — needs cash-flow opportunities, portfolio planning, long-term strategy.

---

## 3. Core Principle: The App Does the Finding

**The client does almost no work.** The client says what he is looking for (or saves a search once); the app finds the deals, scores them, explains them, and builds the action plan. The client only reviews results and acts.

This is a deliberate product decision. There is **no CSV import and no manual list-pulling** required of the user — that was rejected as too much work for the client. The app sources opportunities itself. See Section 12 (Data Sourcing) for how, and what it costs.

---

## 4. Core Product Loop

```
User creates wealth goal
        ↓
AI builds investment strategy
        ↓
App creates Buy Box
        ↓
App searches opportunities  (API + AI browser workers — app does this, not the user)
        ↓
Scores every property
        ↓
Explains opportunity
        ↓
Creates Action Plan
        ↓
User contacts owner
        ↓
Tracks progress
        ↓
Updates Wealth Plan
```

---

## 5. Core Features

### 1. Wealth Planner
**Input:** current income, cash available, credit, target income, target net worth, timeline, preferred strategy.
**Output:** wealth gap, income gap, estimated properties needed, suggested investment strategy, acquisition roadmap.

### 2. Property Explorer
**Search by:** address, ZIP, county, city.
**Filters:** pre-foreclosure (lis pendens), tax delinquent, probate, foreclosure, vacant, high equity, free & clear, land, commercial, multifamily, development, owner occupied, absentee owner.

### 3. Opportunity Score
Every property receives: Overall Score, Strategy Match, Risk Score, Capital Fit, Timeline Fit, Confidence Score.

### 4. Deal Analysis
Every opportunity includes: why it was flagged, strengths, weaknesses, risks, unknowns, estimated upside, recommended strategy, exit options.

### 5. Deal Action Plan
Auto-generated: research checklist, due-diligence checklist, owner-outreach plan, financial checklist, document checklist, negotiation checklist.

### 6. Contact Map
Shows: owner, attorney, county office, tax office, title company, surveyor, contractor, engineer, lender, broker.
Each contact explains: why they matter, questions to ask, documents needed.

### 7. Land Intelligence
Analyzes: vacant land, subdivision opportunities, assemblage, infill lots, commercial land, agricultural land, development potential, environmental risks, utilities, flood zones.

### 8. Financial Calculators
Rental, BRRRR, Flip, Wholesale, Cash Flow, ROI, Cap Rate, NOI, Development, Maximum Offer, Rehab Budget.

### 9. AI Coach
Every page includes coaching. Instead of "Buy this," the AI says:
> Here's why this opportunity exists. Here's what concerns me. Here's what I'd verify before spending a dollar. Here's what I would do next.

### 10. Task Center
Convert recommendations into tasks. Assign due dates. Mark complete. Track deal progress.

### 11. Alerts
Notify when: new tax sale, probate filing, owner changes, price reductions, new opportunity matches, deadline approaching.

### 12. Opportunity Timeline *(premium differentiator)*
Every property gets its own **living history** — the app becomes the investor's institutional memory:

```
Discovered → AI analyzed → Owner identified → Tax records verified →
Called owner → Letter sent → Follow-up → Offer made → Negotiating →
Purchased → Added to portfolio
```

Each step stores its documents, contacts, notes, and the AI's next recommended action. Months later the user can ask *"What happened with the Bowie duplex?"* and get the full history — every call, letter, document, and the recommended next move. This continuity is hard to reproduce manually and is what lifts the app above a property-search tool.

### 13. Deal Playbooks *(guided, per deal type)*
For each deal type — starting with **pre-foreclosure / lis pendens** — the app runs a **step-by-step playbook** that walks the user from the public filing to a signed deal: find → verify property, liens, and equity → understand the owner's situation → reach out lawfully and fairly → make a fair-value offer → get it under contract with the right disclosures → close or assign within state rules. Each step says exactly what to do, who to contact, what to ask, and what to watch for, and drops the next step on the calendar. The playbook **guides and reminds; it does not auto-track deal phases** — the user drives, the app coaches.

**Compliance & fair-dealing guardrails (baked in):**
- Outreach respects Do-Not-Call / TCPA and state solicitation and licensing rules; the app coaches compliant, non-pressure contact only.
- Offers use a **fair-value range, never "just what they owe"**; the app flags equity the owner would give up.
- Flags foreclosure-rescue and equity-purchase laws (mandatory disclosures, rescission rights) and recommends title/attorney review before contracting.
- Flags states that restrict or require disclosure/licensing for **contract assignment / wholesaling**.
- Extra care and plain-language disclosure for owners in active distress. No pressure tactics, ever (ties to Section 8).

---

## 6. Dashboard

Immediately shows: today's opportunities, deals needing attention, upcoming deadlines, tasks, pipeline, wealth progress, portfolio summary, recommended next actions.

---

## 7. Pages

Home · Dashboard · Property Search · Property Details · Wealth Planner · Buy Box · Opportunity Center · Task Center · Contact Map · Land Explorer · Calculators · Portfolio · Settings

---

## 8. AI Personality

Teacher first. Investor second. Dad always.

- Never hype. Never pressure. Always explain.
- Every recommendation includes reasoning.
- Every number explains where it came from.
- **Never fabricate data.**

Clearly separate: **Verified facts · AI analysis · User assumptions · Calculated estimates.** Every data point carries its source (see Section 12 provenance).

---

## 9. Technology Stack

**Frontend:** Next.js · React · Tailwind CSS · TypeScript
**Backend:** Supabase (Postgres, Auth, Storage) · Node.js API routes
**AI:** Claude (Anthropic) as the primary coach/analysis model *(already owned)*. OpenAI optional.
**Maps:** Google Maps or Mapbox
**Property Data:** one licensed API (e.g. BatchData) + AI browser workers for free public county records. See Section 12.
**Browser automation:** Playwright + Chromium (for the AI workers that read public county sites)
**Hosting:** Vercel *(already owned)*

> The user already has Vercel, Supabase, and Claude. The **only new running cost is property data** — see Section 13.

---

## 10. MVP Deliverables

- User authentication (single account)
- Wealth Planner
- Buy Box generator
- Property search
- Property detail page
- Opportunity scoring
- AI deal analysis
- Action plan generation
- Contact map
- Task management
- Saved searches
- Alerts
- Dashboard

---

## 11. Success Metrics

- User creates first Wealth Plan in under 5 minutes.
- User saves first opportunity in under 10 minutes.
- AI analysis generated in under 10 seconds.
- 90% of opportunities include a complete Action Plan.
- User can move from discovery to outreach without leaving the app.

---

## 12. Data Sourcing & Sourcing Capability

This is the section that determines both capability and cost. The design goal: **the app finds the deals, the client does almost nothing, and the running cost stays as low as honestly possible.**

### The model: app-sources, hybrid data

Two workers feed the app, and the app decides which to use per job:

| Job | Who does it | Cost |
|---|---|---|
| **Find distressed lists** (lis pendens / pre-foreclosure, tax-sale, probate, foreclosure, code violations) | **AI browser workers** reading free public county sites | **$0** |
| **Property details / value / rent estimates** | Licensed API (on-demand, gap-fill) | Per lookup, cheap |
| **Owner contact info** (phone, email — skip-trace) | Licensed API | The main real spend |
| **Score / explain / action plan / coaching** | Claude (already owned) | **$0 new** |

**Rule of thumb:** AI browser workers for free public county data; the paid API only for what a browser can't safely or reliably get (chiefly owner skip-trace).

### AI browser workers — what they do and don't touch

- ✅ **Do:** county tax-sale lists, probate dockets, foreclosure notices, code-violation lists, and other records **published free and public by the county.** These are fair game — public by law. Run them on a schedule (e.g. nightly) to keep opportunities fresh.
- ❌ **Don't:** Zillow, Realtor.com, MLS, or any site that bans scraping in its terms. For that class of data, use a licensed API instead. Never point browser workers at sites that prohibit automated access.

### Honest limitations of browser workers

1. **Legal/ToS** — public county records are fine; commercial listing sites are not. Respect each site's terms.
2. **Fragility** — county sites change and break scrapers; CAPTCHAs and IP blocks happen. Each county source is its own small maintenance job. Start with 1–3 target counties, expand deliberately.
3. **Speed** — browser reads take seconds per page (fine for scheduled batch runs, not live clicking). The API is instant when speed matters.

### Data service architecture

All feature code goes through **one `PropertyDataService`** with pluggable adapters:

- `CountyBrowserAdapter` — AI/Playwright workers, per target county (free public records)
- `ApiAdapter` — the licensed vendor (details + skip-trace, paid, gated)
- Future adapters (Regrid for parcels, etc.) drop in without touching feature code.

`getProperty()` runs a waterfall: **cache → free browser/county data → paid API only for the gap.**

### Provenance (non-negotiable — powers "never fabricate data")

Every field stored in Supabase carries `source` (`county` / `browser` / `api` / `ai_estimate` / `user_assumption`) and `retrieved_at`. This:

- lets the AI Coach say exactly where each number came from,
- drives the "Verified facts vs. AI analysis vs. assumptions vs. estimates" separation,
- and tells the waterfall which fields still need a (paid) fetch.

### Paid calls are gated

Since it's one user, the app **never silently spends money.** When only a paid API can answer (e.g. owner phone), the AI Coach asks first: *"Want me to pull the owner's contact info? (~1 credit)"* — the user clicks, it fetches, it caches forever. Optional hard monthly cap (e.g. refuse to spend past $X without confirming).

---

## 13. Cost Model (single user)

The user already owns Vercel, Supabase, and Claude. **The only new cost is property data.**

| Item | Upfront | Monthly | Notes |
|---|---|---|---|
| Vercel / Supabase / Claude | $0 | **$0** | Already owned |
| AI browser workers (county records) | $0 | **$0** | Free public data; costs build/maintenance time, not fees |
| Licensed API — details + skip-trace | $0 | **$20–100** | Pay-per-use, gated behind user click |
| **Total** | **$0** | **~$20–100** | Low end (~$20–40) with browser workers doing the sourcing |

**Plain version:**
- **$0 upfront.**
- **~$100/mo** buys a no-limits solo experience (thousands of records, hundreds of skip-traces, unlimited AI analysis).
- **~$20–40/mo** if AI browser workers handle the free county list-sourcing and the API is used only for owner skip-trace.
- There is **no $0 "app finds the deals" version** — free sourcing only happened when the client pulled lists himself, which was rejected. Taking that work off the client means the data has a price.

Still below PropStream ($99/mo) or DealMachine ($99+/mo), with zero client effort and an AI coaching layer those tools don't have.

---

## 14. Phase 2 — Smart Features

These turn the app from "a database with AI text" into an assistant that works on its own.

### Autonomous nightly agent *(strongest differentiator)*
Instead of making the user search, the app searches for them. On a schedule it:
1. Pulls new county tax-sale data
2. Checks probate filings
3. Looks for ownership changes
4. Compares against the user's Buy Box
5. Scores opportunities
6. Delivers the top opportunities each morning, with explanations

### Learns the user's taste
Track saved deals, ignored deals, purchased deals, filters used, and preferred strategies — then adjust recommendations over time so the Buy Box sharpens to actual behavior.

### AI comps & ARV *(with a hard rule)*
**The AI must not invent comparable sales or fabricate numbers.** The correct pattern:
1. Pull **real** nearby sales (data source, not the model).
2. Compute ARV with **deterministic** calculations.
3. The AI **explains** the estimate and highlights the assumptions behind it.

The AI narrates and flags assumptions; it never manufactures the underlying figures. This upholds the "never fabricate data" principle in Section 8.

### Document reader
Upload deeds, tax bills, title reports, surveys, appraisals, inspection reports, HOA documents, probate filings. The AI summarizes each and extracts the key facts into the deal record and Opportunity Timeline.

---

## 15. What It Replaces vs. Works Alongside

Framed correctly: **the app doesn't replace a person — it automates parts of the investing workflow.**

**The app replaces (real time/cost savings):**
- Manual public-record research
- Deal-analysis spreadsheets
- Lead lists and property research
- Basic underwriting
- Task tracking and follow-up reminders
- Opportunity organization

It reduces or eliminates work typically done by lead researchers, virtual assistants, junior analysts, and administrative coordinators.

**The app works alongside (when the deal needs them):**
- Title companies
- Real estate attorneys
- Lenders / private lenders
- Surveyors, civil engineers
- Contractors, inspectors
- Insurance agents

It does **not** replace attorneys, licensed appraisers, surveyors, inspectors, closing agents, or brokers where their legal role is required.

### On real estate agents specifically
For the deal types this app targets — **tax-delinquent properties, tax liens, tax-deed sales, probate, vacant land, and off-market deals — you generally do not need an agent** to find or buy. The key players are usually:

- County Treasurer / Tax Office
- Tax Sale Administrator
- Clerk of Court
- Probate Court
- Title Company
- Real Estate Attorney (state/transaction dependent)
- Surveyor (for land)
- Civil Engineer (development)
- Contractor
- Insurance Agent
- Lender / private lender

An agent becomes **optional** — needed mainly to list a property after renovating, to buy through the MLS, or for local market expertise. Many investor-to-owner deals go **Opportunity → Due diligence → Purchase agreement → Title company / attorney → Closing** without an agent at all.

**Positioning:** it's not about replacing agents — it's about helping investors **source, evaluate, and execute on off-market opportunities more efficiently.**

---

## 16. Time & Cost Savings

Real Estate Dad eliminates repetitive research, organizes every opportunity, and reduces how many professionals you involve before a deal is ready.

### Time saved per task

| Task | Manual Time | With Real Estate Dad | Time Saved |
|---|---|---|---|
| Research a property | 45–90 min | 5–10 min | 80–90% |
| Analyze a deal | 30–60 min | 5 min | 85% |
| Determine investment strategy | 20–30 min | 2 min | 90% |
| Build due-diligence checklist | 20 min | Instant | 100% |
| Identify who to contact | 30–60 min | 2 min | 90% |
| Prepare outreach | 30 min | 2 min | 90% |
| Organize documents | 20 min | Instant | 100% |
| Track deadlines | Manual | Automatic | 100% |
| Portfolio planning | Several hours | Minutes | 90% |

**Estimated savings per deal: 3–6 hours.** For active investors evaluating 10–20 opportunities/month, that's **30–120 hours saved monthly.**

### Professional cost savings

Reduces the need for outsourced research and administrative work. It does **not** replace licensed professionals where their expertise or legal authority is required.

| Role | Typical Cost | Real Estate Dad |
|---|---|---|
| Virtual Assistant | $500–2,000/mo | Research automated |
| Deal Researcher | $1,000–3,000/mo | Opportunity analysis automated |
| Lead List Research | $300–1,500/mo | Public-record workflows |
| Spreadsheet Management | Several hrs/week | Built into app |
| Follow-up Tracking | Manual | Automated |

---

## 17. Professional Directory by Deal Type

For each opportunity the app identifies who's involved, why they matter, what to ask, and what documents to request. Baseline directory:

**Tax Delinquent Property**
- *Usually required:* County Treasurer / Tax Office · Title Company · Real Estate Attorney (recommended before closing)
- *Sometimes:* Contractor · Insurance Agent · Lender

**Tax Lien Certificate**
- *Usually required:* County Tax Office · Treasurer · Attorney (state dependent)

**Tax Deed Sale**
- *Usually required:* Tax Sale Office · Title Company · Attorney
- *Sometimes:* Surveyor · Contractor

**Probate Property**
- *Usually required:* Probate Court · Personal Representative / Executor · Probate Attorney · Title Company
- *Sometimes:* Contractor · Inspector

**Foreclosure**
- *Usually required:* Trustee or Auction Company · Title Company · Attorney
- *Sometimes:* Lender · Contractor

**Vacant Land**
- *Usually required:* Planning & Zoning · Surveyor · Title Company
- *Depending on project:* Civil Engineer · Environmental Consultant · Utility Providers · Architect

**Development Opportunity**
- *Usually required:* Planning Dept · Zoning Dept · Civil Engineer · Surveyor · Title Company
- *Often:* Architect · General Contractor · Environmental Consultant · Lender · Attorney

**Commercial Property**
- *Usually required:* Title Company · Attorney · Lender
- *Depending on property:* Engineer · Environmental Consultant · Property Inspector

### What the app does for every opportunity
Explains why it matters · recommends the best strategy · builds a due-diligence checklist · identifies the professionals involved and why · generates the questions to ask · lists documents to request · creates tasks and reminders · tracks it from discovery through acquisition.

> This is what makes Real Estate Dad an **operating system for real estate investing**, not just another property-search tool.

---

## 18. Commercial Value & Pricing

Estimates for how the work could be priced (development effort, not the idea):

**Selling the plan (this brief + build prompt):**
- $100–500 as a reusable template
- $500–2,000 as a polished, industry-specific blueprint with research

*(Most value is in what the plan builds, not the plan alone.)*

**Building the custom app (one-time):**
- Basic version: $10k–20k
- Professional version: $20k–50k
- Enterprise version: $50k–150k+

**If sold as SaaS (per seat/month):**
- Solo investor: $99–149/mo
- Professional investor: $199–299/mo
- Team: $399+/mo

**Hybrid model:**
- $2,500 setup + $149/mo (support and data)

For this build (single user), the running cost is only the property data (Section 13); these figures describe what the app and the work are *worth*, not what this user pays to operate it.

---

## 19. Deployment Note

Real Estate Dad is a standalone product. It must live in **its own folder or its own repository**, fully isolated from any unrelated project (e.g. the All Purpose drywall site). It shares no code, routes, or data with any other app.
