# One-Off Worker

**A single worker that does one job, on its own.** You run it whenever you need that
job done. It doesn't depend on any other worker. **This is where most workers start.**

```
        [ Deal Analysis worker ]
```

## When to use
- The job stands alone: "analyze a property," "write a drywall quote," "draft an email."
- You just want *that one thing* done well, on demand.

## How to build it
1. Write the SOP for the job → `../../3-sop/`
2. Fill in the skill file → `../skill-template.md`
3. Test & refine it → `../test-and-refine.md`
4. Activate → save to `.claude/skills/<name>/SKILL.md`

Done. See **`example.md`** for a complete one built end-to-end (Deal Analysis).

> If you find yourself running several one-offs back-to-back in the same order every
> time, that's your signal to look at `../chain/`.
