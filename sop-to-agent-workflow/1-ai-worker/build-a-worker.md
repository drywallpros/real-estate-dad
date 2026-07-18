# Build an AI Worker

An **AI worker** is a job you write down once so Claude does it the same way every
time — you never re-explain it. You build one from an SOP (see `../3-sop/`).

You can build **one worker on its own**, or **chain several together**. Both are here.

---

## First: build ONE worker (the steps)

1. **Start with an SOP.** The plain-English steps for the job. (`../3-sop/`)
2. **Turn it into a skill file.** Copy `skill-template.md` and fill it in:
   Role, Context, Command, Format, Tools, Guardrails. (This is just the SOP written
   the way Claude reads best — see `../2-create-instructions/`.)
3. **Test & refine.** Run it on 3–5 real examples, compare to what "good" looks like,
   fix the instructions until it's right. (`test-and-refine.md`)
4. **Activate.** Save the finished skill to `.claude/skills/<name>/SKILL.md`. Now it's live.

That's a **one-off worker** — a single agent that does one job on demand. Done.
Full worked example: `example.md`.

---

## Then (optional): ONE-OFF vs CHAIN

Once you have workers, there are two ways to run them:

### One-off — a single worker, standalone
```
        [ Deal Analysis worker ]
```
Use it by itself whenever you need that one job done. Most workers start here.
Keep them one-off unless a job truly has multiple stages.

### Chain — several workers, output feeds the next
```
  [ Find Deal ] → [ Analyze ] → [ Action Plan ] → [ Draft Outreach ]
```
Use a chain when one big job has **stages**, and each worker's result is the next
worker's starting point. You "connect them together" so they run as a line.

> There's also a **fan-out** setup — one manager ("Editor") that hands each incoming
> task to the right standalone worker. That's just many one-offs with a router on top.
> Start simple; add chains/routers only when you actually need them.

**Rule of thumb:** independent jobs → keep them **one-off**. Stages of one bigger job
→ **chain** them.

---

## For this repo
Natural first workers for Real Estate Dad: **Deal Analysis**, **Outreach**, **Nightly
Search**. Build each as a one-off first; chain Find → Analyze → Action Plan → Outreach
later if you want it to run end-to-end.
