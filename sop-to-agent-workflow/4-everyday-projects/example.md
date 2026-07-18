# Example B — NON-AGENT PROJECT (just the prompt framework)

**Use case:** a one-time task. You don't need a reusable agent — you need one great
answer, once. So you skip the skill/test/activate pipeline and use only the
**RCCF prompt framework**: Role + Context + Command + Format.

**Task chosen:** "Write the homepage hero + 3 benefit sections for the Real Estate Dad
landing page." (Could just as easily be a drywall bid email, a competitor teardown, a
report — the structure is identical.)

There is **no skill file, no eval set, no orchestration.** You paste the prompt below
into Claude, get the copy, tweak, done.

---

## The paste-and-go prompt

> **ROLE**
> Act as a world-class direct-response copywriter who specializes in conversion for
> software products aimed at everyday, non-expert users.
>
> **CONTEXT**
> The product is "Real Estate Dad," an AI real estate investing platform for ONE
> individual investor (not a SaaS). Unlike PropStream or DealMachine, it doesn't just
> show listings — it explains *why* an opportunity exists, *what strategy* fits, *who*
> to contact, and *what to do next*. It acts like an experienced investing mentor, not a
> chatbot. The audience ranges from total beginners to experienced investors, land
> buyers, wholesalers, and buy-and-hold landlords. The core promise: "the app does the
> finding — you just review and act." Tone: confident, plain-spoken, zero hype, no jargon.
>
> **COMMAND**
> Write landing-page copy with:
> 1. One hero headline (≤ 10 words) + one subhead (≤ 25 words) + one primary CTA button label.
> 2. Three benefit sections, each with a short header (≤ 6 words) and 2 sentences of body.
> 3. Make every benefit about the *outcome for the investor*, not the feature. Make the
>    implicit explicit — name the pain it removes.
>
> **OUTPUT FORMAT**
> ```
> HERO
> Headline:
> Subhead:
> CTA button:
>
> BENEFIT 1
> Header:
> Body:
>
> BENEFIT 2
> Header:
> Body:
>
> BENEFIT 3
> Header:
> Body:
> ```

---

## Why this is the "non-agent" path
- **No Role→skill file** — the role lives in the prompt, used once.
- **No Test & Refine loop** — you eyeball the output and edit it yourself.
- **No orchestration** — nothing connects to anything.

If you found yourself writing this same prompt every week for many products, *that's*
the signal to promote it into a skill (Example A path). One-off → framework only.
Repeated procedure → full pipeline.

---

## The rule, one more time
| You need… | Do this |
|---|---|
| One good answer, once | **RCCF prompt** (this example) |
| A worker that runs the same procedure over and over | **Full pipeline → skill** (Example A) |
