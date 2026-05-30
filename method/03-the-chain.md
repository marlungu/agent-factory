# 03 · The Chain

One agent does one job. A factory connects several into a sequence that does the whole job. The sequence is always the same shape:

```
Research  →  Plan  →  Build  →  Verify  →  Validate
```

Five stages. Every reliable factory follows them, whatever the domain.

## The five stages

**Research** — Understand the work before touching it. Read the inputs, map what exists, surface risks and open questions. Produce findings, not opinions. This agent reads only.

**Plan** — Turn the findings into a clear plan: what needs to happen and how to approach it. This is where direction is set. Still no building — just a decision about what to build. This is the right place for the first human check, because a wrong plan is cheap to fix here and expensive to fix later.

**Build** — Do the actual work, following the approved plan. If the job has two distinct halves that depend on each other, this can be two agents in order — the second reads the first's output and builds on it, rather than guessing.

**Verify** — Prove the work does what the plan said it should. The verifier checks against the plan from the outside. It does not fix what it finds; it reports.

**Validate** — A final, independent check for gaps, quality, and anything the earlier stages missed. It reports only, grouped by how serious each issue is. This is the agent that makes the whole factory trustworthy, because it has no stake in the work looking good.

## Why the order is fixed

Each stage depends on a clean result from the one before. Research feeds the plan. The approved plan feeds the build. The build feeds verification. Skip a stage or run them out of order and you are back to guessing — the exact problem the factory exists to solve.

## How the chain runs

One thing coordinates the sequence: the **orchestrator**. You give it a single instruction — "run the factory on this input" — and it runs each agent in turn, passing each one the clean inputs it needs, stopping only at the human gates.

You do not drive each agent by hand. You start the chain and step in at the few points that need your judgment. Everything else runs on its own.

## The stages are the shape, not the agent count

This is the part people miss: the five stages are the *shape* of the work. They do not mean "every factory has five agents." How many agents you build, and what each one does, depends entirely on your project.

- A simple job might collapse to **three agents** — one to research, one to build, one to check.
- A complex job might need **seven or more** — a research stage split into a reader and a risk-spotter, a build stage split across three specialists, two separate checkers.
- Some projects need **two builders** that hand off to each other. Some need none beyond a single writer.

You build the agents your project needs. A documentation pipeline, a customer-response flow, and a data-cleaning job will each have a different lineup — because the work is different.

What stays constant is the **discipline**, not the headcount: research before building, a plan you approve, a build that follows it, an independent check at the end, and clean handoffs throughout. Map those onto your work with as many or as few agents as the work actually requires.

The example below uses five because that is what a job application needs. Yours will be whatever yours needs.

## See it

In the example factory, the five stages map like this:

| Stage | Agent |
|---|---|
| Research | `researcher` — reads the job posting, extracts requirements |
| Plan | `brief-writer` — turns findings into a role brief → **gate** |
| Build | `resume-tailor` → **gate**, then `cover-letter-writer` |
| Verify + Validate | `evaluator` — scores fit, flags gaps, go/no-go → **gate** |

Notice the example has four agents, not five: the `evaluator` does verify and validate together. That is on purpose. In software, a verifier runs the tests and a validator checks the result against the plan — two jobs. In this domain there is nothing to "run," so one agent covers both. This is the agent-count point in action: you combine stages when the work lets you.

The orchestrator that wires them is in `../example/job-application-factory/.claude/skills/job-application-factory/SKILL.md`.

Next: `04-human-gates.md` — where you stay in control, and where you should not.
