# SOP → AI Agent Workflow

A playbook for turning business SOPs into working AI agents with Claude — plus the
prompt habits you use on every project. Everything is organized **by purpose**, in the
order you'd actually use it.

---

## Start here

**Not sure which approach you need?** → **[`1-start-here/which-path.md`](1-start-here/which-path.md)**

It sorts any task into one of three lanes:

| Lane | You're doing… | Folder |
|---|---|---|
| **A** | One good answer, once | `2-prompt-framework/` |
| **B** | Building an app / website / cron job | *your normal project folders — not here* |
| **C** | Building a reusable AI worker | `3-build-ai-workers/` |

The prompt framework (Lane A) is also the tool you use *inside* Lanes B and C.

---

## The folders, by purpose

### `1-start-here/` — decide
- **which-path.md** — the decision guide: which of the three lanes am I in?

### `2-prompt-framework/` — how to talk to Claude *(used in every project)*
- **framework.md** — the Role + Context + Command + Format (RCCF) method explained.
- **sample-prompt.md** — copy-paste skeleton + filled samples (real estate + drywall).

### `3-build-ai-workers/` — how to build a team of Claudes *(agents only)*
- **pipeline.md** — the full SOP → skill → test → agent pipeline + the two orchestration shapes.
- **skill-template.md** — copy this once per SOP to write a skill.
- **test-and-refine.md** — checklist to graduate a skill to an "active agent."

### `4-examples/` — worked end-to-end examples
- **example-A-ai-agent-skill.md** — full pipeline turning the Deal Analysis SOP into a real skill.
- **example-B-non-agent-prompt.md** — the same framework as a one-off prompt (no agent).

---

## The one-sentence mental model

- **Prompt framework** (folder 2) = how you *talk to Claude*. Used everywhere.
- **The pipeline** (folder 3) = how you *build a team of Claudes*. Used only when the thing you're building is itself an AI agent.
