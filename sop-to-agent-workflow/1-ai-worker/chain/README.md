# Chain of Workers

**Several workers connected in a line, where each one's output becomes the next one's
input.** Use this when one big job has **stages** that hand off to each other.

```
  [ Find Deal ] → [ Analyze ] → [ Action Plan ] → [ Draft Outreach ]
       │              │               │                  │
    a property   →  a verdict   →   a plan       →    an email
```

## When to use
- One large job breaks into steps, and step 2 needs step 1's result.
- You want it to run start-to-finish without you handing things off manually.

## How to build it
1. Build each worker **as its own one-off first** (see `../one-off/`). Get each one
   working alone before connecting anything.
2. Decide the order and what passes between them (the output of one = the input of the next).
3. Connect them so they run as a line.

> **Also worth knowing — fan-out:** instead of a line, one manager worker (an "Editor")
> can hand each incoming task to the right standalone worker. That's just many one-offs
> with a router on top. Use a chain for *stages of one job*; use fan-out for *routing
> different jobs*. Start simple — add either only when you actually need it.

See **`example.md`** for a chain built for Real Estate Dad.
