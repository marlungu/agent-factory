# 01 · The Problem

You ask one AI chat to build something. It feels like magic on day one. By week four you are spending more time supervising it than the work would have taken you alone.

This is not the model failing. It is the structure failing.

## What goes wrong

When you type "do this whole job" into one chat, you are asking a single session to be the researcher, the planner, the builder, the checker, and the reviewer — all at once, in the same conversation.

So this happens:

- A wrong assumption enters early.
- The chat keeps building on top of it.
- The mistake spreads into everything downstream.
- By the time you notice, it is in ten places.

The work all happens in one context window, so the early noise — the false starts, the half-formed guesses, the abandoned attempts — stays in view and muddies every later step. The model is reasoning through a cluttered room.

## Why "just correct it" does not fix it

When the chat makes a wrong turn, the natural move is to say "no, do it this way" and let it patch. But now both the wrong version and the correction live in the same context. The model carries both. Small corrections pile up into a session that is mostly cleanup.

A clean session with the right starting assumption beats a patched session every time.

## The shift

Real teams do not work in one big conversation. Different people own different jobs. Someone clarifies the problem. Someone plans. Someone builds. Someone checks. Each works in their own head, with their own focus, handing off a clean result.

The fix is to structure AI work the same way: **split the job across specialist agents, each with one focused task and its own clean context.** Coordinate them in order. Keep a human at the decisions that matter.

That structure is a **factory**. The rest of this method shows you how to build one.

Next: `02-the-agent.md` — what a single agent is, and the three things that make it work.
