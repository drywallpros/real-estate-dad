---
name: <skill-name-in-kebab-case>
description: <One sentence: what this skill does and when to trigger it. Be specific — this is what makes the agent pick it up at the right time.>
---

# <Skill Title>

## Role
<Who the agent should be. One or two sentences. Narrow it.>
> Example: "You are a disciplined real estate deal analyst who values capital preservation over optimism."

## Context
<Everything the agent needs to know to do the job: background, definitions,
where inputs come from, examples of good work, constraints of the business.
The more relevant context, the better it performs.>

- Input(s) it receives:
- Reference material / examples:
- Business rules that always apply:

## Command
<Step-by-step, explicit instructions. Make the implicit explicit. Number the steps.>
1.
2.
3.

## Output Format
<The exact shape of the result. Give a template so it can't wander.>
```
<paste the exact table / bullet structure / JSON / document layout you want>
```

## Tools
<What the agent may use to do the work.>
- [ ] File system
- [ ] Data API(s): <name>
- [ ] Spreadsheet / docs
- [ ] Web / search
- [ ] Other:

## Guardrails
<What it must never do. Be blunt.>
- Never invent numbers — if data is missing, say so.
- Only use approved sources: <list>.
- Do not <action that would be harmful/off-limits>.

## Definition of Done (eval)
<How you'll know the skill works. List 3–5 real test inputs and their known-good outputs.>
| # | Input | Expected output |
|---|-------|-----------------|
| 1 |       |                 |
| 2 |       |                 |
| 3 |       |                 |
