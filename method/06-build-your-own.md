# 06 · Build Your Own

You understand the method. Now point it at your own work. You will not start from a blank page — you will copy the example factory and change four things.

## First: pick the right job

A good first factory is work that is:

- **Repetitive** — you do it often enough that the structure pays off.
- **Multi-step** — it has stages, not one single action.
- **Judgment-bearing** — you would want to check it at a point or two, not blindly trust it.

Good first candidates: meeting notes into a follow-up plan, a customer complaint into a drafted reply, a rough idea into a one-page proposal, raw research into a briefing.

Avoid for your first one: work with no clear stages, or work you would never review. The gates are the value — pick a job where a checkpoint makes sense.

## Start from the example

Copy `example/job-application-factory/` to a new folder and rename it. You now have a working factory to reshape. Change these four things, in this order.

### 1 · The shared memory (CLAUDE.md)

Rewrite it to describe your job: what the factory does, what the input and output files are, the agent chain, and the hard rules. Keep the "never invent / never guess" rules — they carry over to almost any domain.

### 2 · The agents

Each agent is one file in `.claude/agents/`. Keep the shape, change the role. Map your job onto the five stages:

| Stage | Your version |
|---|---|
| Research | reads your raw input, extracts what matters |
| Plan | turns findings into a plan → **gate** |
| Build | produces your main work product → **gate** |
| (second build) | a follow-on piece that depends on the first — or delete it |
| Validate | checks the result honestly → **gate** |

You do not need exactly five agents. The number is yours to decide, per project. The job application needs five; a simpler job needs three; a complex one needs more. Design the lineup around your work, not around this example. But keep **at least one reader at the start and one checker at the end** — those two are what make it a factory and not a single prompt.

For each agent, get four things right:
- **one job** — if you can describe it with "and," split it in two
- **clean inputs** — list exactly which files it reads, nothing more
- **the right tools** — readers get read-only tools; only builders get write tools; checkers never get write tools
- **a hard boundary** — spend real effort on the "cannot do" list; it matters most

The fastest way to write one: open Claude Code in your copied folder and run `/agents`. It walks you through it and writes the file. Then tighten the "cannot do" list by hand — the generator keeps it loose.

### 3 · The orchestrator

One file: `.claude/skills/<your-factory>/SKILL.md`. It lists the agents in order and marks where the human gates are. Change the names, the file paths, and where you stop for approval. Keep the rules at the bottom — they are what stop one agent from doing another's job.

### 4 · The inputs

Replace the files in `input/` with whatever your job starts from. Name them plainly. Add sample inputs so the factory runs out of the box for anyone you share it with.

## Run, watch, tune

Run your factory on a real example. Watch where it stumbles. When something surprises you, do not patch it in the moment — add a rule to CLAUDE.md so it never happens again. After a few runs, the factory knows your work.

## Restart note

Claude Code loads agents when a session starts. If you add or change an agent file mid-session, restart the session so it loads.

## The discipline, one more time

One job per agent. Clean context. A hard boundary. A human at the gates. A memory that learns.

Keep those five. Change everything else. That is the framework — and now it is yours.
