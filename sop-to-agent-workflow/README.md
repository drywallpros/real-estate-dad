# SOP → AI Agent Workflow

A repeatable method for turning any business SOP (Standard Operating Procedure)
into a working AI agent, using Claude skills.

This folder is the "how we build AI workers" playbook. Drop an SOP in, follow the
pipeline, and out comes a tested skill an agent can run.

---

## Can I use this for all my projects, or only for AI workers?

**Both — but be precise about what "this" means.** There are two things on the
diagram, and they have different reach:

| Piece | Use it for… |
|---|---|
| **The prompt framework** (Role + Context + Command + Output Format) | **Every project, every prompt.** This is a universal habit. Any time you ask Claude for anything — a bid, a report, a code change, a marketing plan — this structure makes the output better. Not AI-worker-specific. |
| **The full pipeline** (SOP → Skill file → Test & Refine → Active Agent → connect them) | **Specifically for building AI workers / agents.** This is the process you run when the goal is a *reusable, automated* worker that executes a procedure over and over, not a one-off answer. |

**Rule of thumb:**
- One-time task → just use the **prompt framework** and ask.
- A procedure you repeat, or want an agent to own → run the **full pipeline** and make it a skill.

And it is **domain-agnostic**. Nothing here is tied to real estate — the same
pipeline builds a drywall-bidding agent, a content-engine agent, or a
deal-analysis agent. You've already got skills in this account (`all-purpose-bid`,
`tagglefish-content-engine`, `docx`) that are exactly this pattern applied to
different businesses.

---

## The pipeline (what the diagram shows)

```
        WORKFLOW / SOP           ← the human procedure, written down
              ↓
     SKILL MARKDOWN FILE         ← Role + Context + Command + Output + Tools + Guardrails
              ↓
      TEST & REFINE SKILL        ← run it on real examples, fix gaps, define "done"
              ↓
       ACTIVE AI AGENT           ← the skill goes live
              ↓
   connect them all together     ← an orchestrator routes between agents
```

Repeat once per SOP. Five SOPs → five skills → five agents, coordinated by one
**Editor / orchestrator** at the top.

---

## The prompt framework (the RCCF pattern)

Every skill instruction — and honestly every good prompt — has four parts:

1. **Role** — *who Claude should be.* Narrows all of its knowledge to the slice you need.
   > "Act like a world-class conversion-focused marketing strategist for software."
2. **Context** — *everything it needs to know.* Transcripts, docs, specs, examples, background. The more relevant context, the better it performs.
3. **Command** — *what to do, explicitly.* Make the implicit explicit. Don't hint — tell it.
4. **Output Format** — *the exact shape of the result.* Bullet list? Table? CSV? PDF? Give it a template and it can't wander outside it.

> Note: the slide labeled the 4th box "Command" too — it's really **Output Format**.
> The clean name for the framework is **Role + Context + Command + Format**.

Two things the diagram leaves out that you should always add to a skill:

5. **Tools** — what the agent is allowed to use (a data API, a spreadsheet, email, the file system). Without this, an "agent" is just a chatbot.
6. **Guardrails** — what it must never do (don't invent numbers, don't contact sellers, only use county public records, etc.).

---

## How to build one (step by step)

1. **Write the SOP in plain English.** How does a human do this task today, start to finish?
2. **Decompose.** Cut it at natural seams so each skill does *one* job well. Too broad = vague; too granular = handoff soup.
3. **Fill the template.** Copy `templates/skill-template.md` and fill in Role, Context, Command, Output, Tools, Guardrails.
4. **Build an eval set.** Grab 3–5 real inputs with known-good outputs. This is your definition of "done."
5. **Test & refine.** Run the skill on the eval set, compare to known-good, fix the instructions. Repeat until it passes.
6. **Activate.** Move the finished skill into place (e.g. `.claude/skills/<name>/SKILL.md`).
7. **Connect.** Once you have several, add an orchestrator that decides which agent runs when and passes outputs between them.

---

## Folder layout

```
sop-to-agent-workflow/
├── README.md                    ← this file (the method + your question answered)
├── templates/
│   └── skill-template.md        ← copy this per SOP
├── skills/                      ← finished skill files land here
└── TEST_AND_REFINE.md           ← the checklist for graduating a skill to "active"
```

---

## For this repo specifically

Real Estate Dad is already an agent system. Natural first SOPs to convert:

- **Deal Analysis** — property in → scored opportunity + strategy + next action out.
- **Contact Map / outreach** — motivated seller in → who to contact + outreach plan out.
- **Nightly search agent** — criteria in → matched deals + alert out.

Each is one skill. Build them with this pipeline, then let the Editor orchestrate.
