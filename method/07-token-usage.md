# 07 · Token Usage

A note on how many tokens the factory uses, why, and when it matters. Written from a real run of the example factory. Optional reading — useful once you start running a factory often or at scale.

## What a real run used

Five agents, reported per-agent tokens from one full run:

| Agent | Tokens |
|---|---|
| Researcher | 6,000 |
| Brief Writer | 9,300 |
| Resume Tailor | 10,000 |
| Cover Letter Writer | 9,600 |
| Evaluator | 13,900 |
| **Total** | **~49,000** |

## Why it is more than a single chat would use

Each agent works at its own clean desk and reads its inputs from scratch. The Brief Writer re-reads the research. The Resume Tailor re-reads the brief and the resume. The Evaluator reads all four prior outputs to judge the package. The same context flows through several agents, so it gets read more than once.

A single chat doing the whole job would load that context once and reuse it — fewer tokens. The factory pays a premium for separating the work.

That premium is the point, not waste. Separate desks are why the factory caught the vendor placeholders and the email mismatch in the test run. A single muddy chat would likely have shipped them. You are trading tokens for reliability and for catching mistakes early.

## Is ~49k "a lot"? Depends on the frame

- **As raw tokens:** modest. A long coding session uses far more. This is a small job.
- **As cost on a Pro/Max plan:** invisible. It is usage already covered by the plan, not metered per token. A workshop attendee on Pro sees no bill.
- **As cost on the API (pay per token):** a few cents at Sonnet rates. Small.
- **As pure efficiency:** if the only goal were the cheapest possible result, one chat is cheaper — but you lose the error-catching.

## When to care, and what to do

For a workshop or occasional use: do not optimize. The clean structure is the lesson and the cost is negligible.

For production factories run hundreds of times on metered API: token discipline matters. The levers, in order of impact:

1. **Pass summaries, not whole files, between agents.** Hand the next agent a tight summary of what it needs instead of the full prior document. Biggest saver.
2. **Trim each agent's inputs to only what it needs.** Example: the Cover Letter Writer does not need the research file — only the brief and the tailored resume. Cutting unneeded inputs cuts tokens directly.
3. **Keep CLAUDE.md short.** Every agent reads it every run, so every line is paid for once per agent. Lean memory pays off five times over.
4. **Watch the heaviest agent.** Here it was the Evaluator at 13.9k, because it re-reads everything. Some of that is necessary (it must see the whole package to judge it); some is not (it may not need the full research file, just the requirements).

## The one-line takeaway

The factory uses more tokens than one chat on purpose — clean context is what makes the output trustworthy. On a plan, the cost is invisible. On metered API at scale, trim by passing summaries instead of whole files and giving each agent only the inputs it needs.