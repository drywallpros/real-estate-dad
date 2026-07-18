# Test & Refine — graduating a skill to "Active Agent"

A skill is not "done" because it produced *an* answer. It's done when it
produces the *right* answer on real inputs, repeatably. Use this checklist
before you call any agent active.

## 1. Build the eval set (do this first)
- [ ] Collected 3–5 **real** inputs (not made-up ones).
- [ ] Wrote the **known-good output** for each — what a good human would produce.
- [ ] These live in the skill's "Definition of Done" table.

## 2. Run it cold
- [ ] Ran the skill on each eval input in a fresh session (no leading hints).
- [ ] Compared each result to the known-good output.
- [ ] Noted every gap: wrong format, missing step, invented data, wrong tone.

## 3. Refine the instructions (not the output)
Fix the **skill file**, not the individual answer. Common fixes:
- [ ] Ambiguous command → made a step explicit / numbered it.
- [ ] Wrong shape → tightened the Output Format template.
- [ ] Hallucinated data → added a Guardrail ("if missing, say so").
- [ ] Missed context → added the reference material it needed.
- [ ] Did too much → split into a second skill.

## 4. Re-run until stable
- [ ] Passes all eval inputs.
- [ ] Passes a **new** input it hasn't seen (didn't just memorize the evals).
- [ ] Output is consistent across 2–3 runs of the same input.

## 5. Activate
- [ ] Moved the finished skill to its live location (e.g. `.claude/skills/<name>/SKILL.md`).
- [ ] `description` is specific enough that the agent triggers it at the right moment.

## 6. Connect (once you have several)
- [ ] Defined which agent runs when (the orchestrator / Editor).
- [ ] Defined how one agent's output becomes the next agent's input.
- [ ] Defined what happens on failure (retry, escalate to human, stop).

---
**Signs you're not done yet:** it works "usually," you keep re-explaining it in
chat, the format drifts between runs, or it confidently makes up data. All three
are instruction problems — fix the file, not the reply.
