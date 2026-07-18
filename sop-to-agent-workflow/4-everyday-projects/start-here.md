# Everyday Projects

This is for **normal work that is NOT an AI worker** — building an app or website,
writing a cron job/script, or just getting a one-time answer. Most of what you do
day to day lives here. No skills, no agents, no pipeline.

---

## What counts as "everyday"?

- **Building an app or website** — Claude writes the actual code into your project.
- **A cron job or script** — a scheduled task (it's just plumbing, not an agent).
- **A one-time ask** — write an email, draft a quote, analyze one thing, once.

If it's a job you'll repeat many times and want automated → that's an **AI worker**
instead (`../1-ai-worker/`), not this folder.

---

## How you actually do everyday work

You don't need anything special — you just **write a good instruction** and let Claude
do it. The only skill is wording the instruction well:

1. **Who to be** — "act as a senior web developer"
2. **What it needs to know** — the feature, the stack, the details
3. **What to do** — the actual task
4. **What the result should look like** — the files, the format, the layout

That's the same 4-part method from `../2-create-instructions/`. Use it to tell Claude
to build the app, write the script, or answer the question.

**Where the work lands:** normal project folders — the app's `src/` or `app/`, a
`scripts/` folder for the cron job — **not in this playbook folder.**

See `example.md` for a filled-in one-off prompt.

---

## Quick sort

| You want… | Go to |
|---|---|
| Build an app/website/script, or a one-time answer | **here** — write an instruction, let Claude build/answer |
| A job done the same way over and over, automated | `../1-ai-worker/` |
| Help wording any instruction | `../2-create-instructions/` |
