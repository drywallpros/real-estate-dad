# Chain Example — Real Estate Dad end-to-end

Four workers connected so a raw property comes in one end and a ready-to-send outreach
email comes out the other. Each worker is built as its own one-off first, then wired
in order.

```
[ Find Deal ] → [ Analyze ] → [ Action Plan ] → [ Draft Outreach ]
```

| # | Worker | Gets IN | Gives OUT (→ feeds next) |
|---|--------|---------|--------------------------|
| 1 | **Find Deal** | Your buy-box criteria | A property + its data (address, price, ARV, rent) |
| 2 | **Analyze** | That property's data | A verdict: GO/WATCH/NO-GO + best strategy + score |
| 3 | **Action Plan** | A GO/WATCH deal | The next steps + who to contact |
| 4 | **Draft Outreach** | The contact + plan | A ready-to-send email/message |

## How the hand-off works
- Worker 2 (**Analyze**) is exactly the one-off in `../one-off/example.md`. In the chain,
  its **output** (the verdict block) becomes worker 3's **input** — nothing is re-typed.
- If worker 2 says **NO-GO**, the chain stops there — no point planning outreach on a
  dead deal. (That's a rule you build into the connection.)

## Build order
1. Build **Analyze** first (the one-off) — it's the core.
2. Build **Find Deal**, **Action Plan**, **Draft Outreach** each as their own one-offs.
3. Connect them in the order above, passing each output to the next.

> Don't build the chain first. Get each worker solid on its own, *then* connect. A chain
> is only as reliable as its weakest worker.
