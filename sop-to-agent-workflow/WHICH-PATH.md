# Which path do I use? (Read this first)

There are **three different kinds of work**, and only ONE of them uses this
`sop-to-agent-workflow` folder. Don't overthink it — find your row.

| What you're doing | Which path | Where the work lives |
|---|---|---|
| **1. One good answer, once** (write copy, draft an email, analyze one thing) | **RCCF prompt** — `templates/rccf-prompt.md` | Nowhere. You paste, get the answer, done. |
| **2. Build software** (an app, a website, a cron job, a script) | **RCCF prompt to *direct Claude to write code*** | Your normal project folders (`src/`, repo root, etc.) — **NOT this folder.** |
| **3. Build a reusable AI worker** (an agent that runs a procedure over and over) | **Full pipeline** — this whole folder | `.claude/skills/` once activated. |

---

## "I want to build an app / website / cron job — which folder?"

**None in here.** That's **Path 2 = normal software development.** This folder
(`sop-to-agent-workflow`) is a special-case toolkit *only* for making AI agents.
Building an app is regular engineering — you don't need skills, agents, test-&-refine,
or orchestration.

What you actually do for Path 2:
1. Use the **RCCF prompt framework** to tell Claude what to build (Role = "senior
   Next.js engineer", Context = the feature + stack, Command = build X, Format = the
   files/structure you want).
2. Claude writes the **actual code** into your project's real folders — the app's
   `src/`, `app/`, a `scripts/` folder for the cron job, etc.
3. The output is **working software**, not a markdown skill file.

> A cron job is a great example: it's just a scheduled script (Path 2). It only becomes
> an "AI worker" (Path 3) if the scheduled thing *is an agent running a skill* — e.g.
> "every night, run the deal-analysis skill on new listings." The schedule is plumbing;
> the agent is the worker.

---

## The clean mental model

- **RCCF prompt framework** = how you *talk to Claude*. You use it in **all three paths**.
- **This folder's pipeline** = how you *build a team of Claudes*. You use it in **Path 3 only.**

So: building your website? Use the framework, point Claude at your codebase, and let it
write code. Come back to this folder **only** when the thing you're building is itself an
AI agent.

---

## Where things go (this repo)

```
real-estate-dad/
├── src/ or app/                 ← Path 2: the actual app & website code lives here
├── scripts/                     ← Path 2: cron jobs / scheduled scripts
├── .claude/skills/              ← Path 3: activated AI workers (finished skills)
└── sop-to-agent-workflow/       ← Path 3: the playbook for BUILDING those workers
```
