# Building AI Workers — the Pipeline

**Purpose:** the full method for turning a business SOP into a working, reusable AI
agent. Use this ONLY when you're building an AI worker (a procedure you repeat and
want an agent to own) — not for one-off answers or normal app/website building.

---

## The pipeline (per SOP)

```
        WORKFLOW / SOP           ← the human procedure, written down
              ↓
     SKILL MARKDOWN FILE         ← Role + Context + Command + Format + Tools + Guardrails
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

## How to build one (step by step)

1. **Write the SOP in plain English.** How does a human do this task today, start to finish?
2. **Decompose.** Cut it at natural seams so each skill does *one* job well. Too broad = vague; too granular = handoff soup.
3. **Fill the template.** Copy `skill-template.md` and fill in Role, Context, Command, Format, Tools, Guardrails.
4. **Build an eval set.** Grab 3–5 real inputs with known-good outputs. This is your definition of "done."
5. **Test & refine.** Run the skill on the eval set, compare to known-good, fix the instructions. Repeat until it passes. (Checklist: `test-and-refine.md`.)
6. **Activate.** Move the finished skill into place (e.g. `.claude/skills/<name>/SKILL.md`).
7. **Connect.** Once you have several, add an orchestrator that decides which agent runs when and passes outputs between them.

---

## The two orchestration shapes

Same build pipeline every time. What changes is **how you wire finished agents together**.

### Shape A — Fan-out (parallel): one Editor → many independent agents

```
                    EDITOR / ORCHESTRATOR
        ┌───────┬───────┼───────┬───────┐
        ↓       ↓       ↓       ↓       ↓
     Agent1  Agent2  Agent3  Agent4  Agent5      ← each owns one SOP
```

- The Editor **routes** each incoming task to the right specialist agent.
- Agents are **independent** — they don't depend on each other's output.
- Best when tasks are **separate** (analyze a deal vs draft outreach vs nightly search).

### Shape B — Chain (sequential): agent → agent → agent

```
   Agent1 → Agent2 → Agent3 → Agent4    (output of one feeds the next)
```

- Each agent's **output becomes the next agent's input** — a pipeline.
- Best when tasks are **stages of one bigger job** (find deal → analyze → action plan → outreach).

**Which?** Independent jobs → Shape A. Stages of one job → Shape B. Real systems mix
both: an Editor fans out to specialists, and *inside* one branch a few agents chain.

---

## For this repo specifically

Real Estate Dad is already an agent system. Natural first SOPs to convert:

- **Deal Analysis** — property in → scored opportunity + strategy + next action out. (Worked example: `../4-examples/example-A-ai-agent-skill.md`.)
- **Contact Map / outreach** — motivated seller in → who to contact + outreach plan out.
- **Nightly search agent** — criteria in → matched deals + alert out.

Each is one skill. Build them with this pipeline, then let the Editor orchestrate.
