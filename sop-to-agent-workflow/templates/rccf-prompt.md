# RCCF Sample Prompt — Role + Context + Command + Format

The prompt framework from slide 3. Copy the skeleton, fill the four blanks, paste
into Claude. Two filled samples below show it working across different jobs.

---

## The blank skeleton (copy this)

```
ROLE
Act as <who Claude should be — the specific expert for this job>.

CONTEXT
<Everything Claude needs to know: the situation, background, the product/business,
the audience, any rules or facts, examples of "good." The more relevant detail, the better.>

COMMAND
<Exactly what to do. Number the steps. Make the implicit explicit — don't hint, tell.>
1.
2.
3.

FORMAT
<The exact shape of the answer. Give a template and it can't wander outside it.>
```

---

## Filled sample #1 — real estate (one-off)

```
ROLE
Act as a disciplined real estate investing mentor who explains decisions in plain English.

CONTEXT
I'm looking at a single-family house: asking $180,000, estimated after-repair value
$260,000, repairs about $35,000, market rent $1,650/mo, taxes $2,400/yr. I invest for
either a flip (want ≥ $25k profit) or a rental (want ≥ $200/mo cash flow after expenses).
I care about capital preservation — talk me OUT of thin deals.

COMMAND
1. Work out the flip profit and the monthly rental cash flow using the numbers above.
2. Tell me which strategy (if any) clears my bar, and by how much.
3. Give me a clear GO / WATCH / NO-GO and the single next action.

FORMAT
VERDICT: <GO / WATCH / NO-GO>
BEST STRATEGY: <flip / rental / none>
FLIP MATH: <one line with the numbers>
RENTAL MATH: <one line with the numbers>
WHY: <2 sentences>
NEXT ACTION: <one step>
```

## Filled sample #2 — drywall business (one-off, different domain)

```
ROLE
Act as a seasoned construction estimator writing a clear, professional client email.

CONTEXT
All Purpose Anytime Services (drywall & finish). A homeowner asked for a quote to hang
and finish drywall in a 20x24 ft garage, walls and ceiling, Level 4 finish, ready for
paint. Our rate covers materials + labor. Phone for questions: 240-300-0555. Tone:
friendly, confident, no jargon the homeowner won't understand.

COMMAND
1. Write a short cover email that thanks them and states the scope in one line.
2. Give a simple line-item breakdown (hang, tape/finish, materials) with a total.
3. State timeline and what we need from them to book. Keep it under 200 words.

FORMAT
Subject: <line>
Body:
<greeting>
<scope sentence>
<line items + total>
<timeline + next step>
<sign-off with phone>
```

---

## Why this works
- **Role** narrows Claude to the right expert instead of a generic assistant.
- **Context** removes guessing — it acts on your facts, not made-up ones.
- **Command** removes ambiguity — numbered steps = nothing skipped.
- **Format** locks the output shape — you get the same clean structure every time.

Notice sample #1 and #2 are totally different businesses but the **four headers never
change.** That's the point: one framework, every project. When you find yourself pasting
the same filled prompt over and over, promote it into a skill (see `examples/EXAMPLE-A`).
