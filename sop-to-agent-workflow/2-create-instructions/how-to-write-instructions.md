# The Prompt Framework — Role + Context + Command + Format (RCCF)

**Purpose:** how to write ONE good instruction to Claude. This is the smallest
building block. You use it in *every* kind of work — one-off answers, building apps,
and building AI workers.

It answers one question: *"How do I phrase what I want so Claude nails it the first time?"*

---

## The four parts

1. **Role** — *who Claude should be.* Narrows all of its knowledge to the slice you need.
   > "Act like a world-class conversion-focused marketing strategist for software."
2. **Context** — *everything it needs to know.* Transcripts, docs, specs, examples, background. The more relevant context, the better it performs.
3. **Command** — *what to do, explicitly.* Make the implicit explicit. Don't hint — tell it.
4. **Format** — *the exact shape of the result.* Bullet list? Table? CSV? PDF? Give it a template and it can't wander outside it.

> The original slide labeled the 4th box "Command" too — it's really **Format**.
> Clean name: **Role + Context + Command + Format (RCCF)**.

## Two more parts once it becomes an agent

When you promote a prompt into a reusable AI worker (see `../3-build-ai-workers/`),
always add:

5. **Tools** — what the agent is allowed to use (a data API, a spreadsheet, email, the file system). Without this, an "agent" is just a chatbot.
6. **Guardrails** — what it must never do (don't invent numbers, don't contact sellers, only use approved sources, etc.).

---

## Why it works
- **Role** narrows Claude to the right expert instead of a generic assistant.
- **Context** removes guessing — it acts on your facts, not made-up ones.
- **Command** removes ambiguity — numbered steps = nothing skipped.
- **Format** locks the output shape — same clean structure every time.

➡️ **Copy-paste skeleton and filled examples:** see `sample-prompt.md` in this folder.
