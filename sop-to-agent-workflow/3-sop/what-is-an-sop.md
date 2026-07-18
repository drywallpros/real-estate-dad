# SOP — the starting point for everything

**SOP = Standard Operating Procedure.** It's just the plain-English steps for how a
job gets done. Nothing technical. If you can explain a task to a new employee, you can
write an SOP.

This is **step 1** of building an AI worker. You can't turn a job into an AI worker
until you've written down how the job actually works. Garbage SOP → garbage worker.

---

## What a good SOP looks like

- **One job per SOP.** "Analyze a property." Not "run the whole business."
- **Written like you're training a person.** Numbered steps, start to finish.
- **Includes the rules.** The minimums, the do's and don'ts, what "good" looks like.
- **Names what goes in and what comes out.** Input → steps → result.

## How to write one

1. Pick one job you do over and over.
2. Walk through it out loud, as if teaching someone. Write each step.
3. Add the rules you follow without thinking ("never guess a number," "always
   double-check comps").
4. Say what the finished result should look like.

That's it. Use `sop-template.md` in this folder to fill in the blanks.

---

## Where the SOP goes next

- If this is a job you want Claude to do **over and over** → take the SOP into
  **`../1-ai-worker/`** and turn it into an AI worker.
- If it's a **one-time** thing → you don't even need an SOP; just write a good
  instruction (**`../2-create-instructions/`**).

> Write SOPs here as you think of them. They're the raw material. Each one can later
> become an AI worker.
