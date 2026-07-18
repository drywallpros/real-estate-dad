# AI Worker

An **AI worker** is a job you write down once so Claude does it the same way every
time — you never re-explain it. You build one from an SOP (see `../3-sop/`).

There are **two kinds**, and each has its own folder:

| Folder | What it is | Use when… |
|---|---|---|
| **`one-off/`** | A single worker that does one job on its own | The job stands alone (analyze a property, write a quote) |
| **`chain/`** | Several workers connected in a line, output feeds the next | One big job has stages (find → analyze → plan → outreach) |

**Start with `one-off/`.** Most workers are one-offs. Only build a `chain/` when a job
truly has multiple stages that hand off to each other.

---

## Shared tools (used by both)

Both a one-off worker and each worker in a chain are built the same way:

1. **`../3-sop/`** — write the job down in plain English.
2. **`skill-template.md`** (in this folder) — turn the SOP into a skill file
   (Role · Context · Command · Format · Tools · Guardrails).
3. **`test-and-refine.md`** (in this folder) — run it on real examples, fix it until it's right.
4. **Activate** — save to `.claude/skills/<name>/SKILL.md`.

A **one-off** stops after step 4. A **chain** does this for each worker, then connects them.
