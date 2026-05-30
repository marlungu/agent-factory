# 02 · The Agent

A factory is made of agents. Get the agent right and the rest follows. Every working agent has three things.

## 1 · One job

An agent does a single task. Not "research and write." Just research. Or just write. Or just check.

This sounds limiting. It is the opposite. An agent with one job has nothing competing for its attention. It does that one thing well, and you always know what it is responsible for.

The moment an agent has two jobs, its focus splits, its context fills with two kinds of work, and mistakes start hiding between them.

## 2 · Clean context

Each agent gets its own fresh workspace. It does not inherit the clutter of everything that came before — only the specific inputs it needs, handed to it directly.

This is the part one-chat workflows cannot do. In a factory, the researcher's dead ends and false starts never reach the builder. The builder sees only the clean result it needs. Every agent reasons in a clear room.

In practice: when one agent finishes, it does not dump its whole thought process onto the next. It passes forward a clean output file. The next agent reads that file and nothing else.

## 3 · A hard boundary

Every agent has an explicit list of what it **cannot** do. This matters as much as what it can do.

- A researcher can read, but **cannot write or change anything**.
- A builder can write its own part, but **cannot touch another agent's**.
- A checker can read and report, but **cannot fix anything it finds**.

The boundary is what makes the output trustworthy. A checker that cannot edit is a checker you can believe, because it has no way to quietly fix-and-hide a problem. A self-graded paper is worthless; a separate grader is honest.

The boundary also stops mistakes from spreading. A builder that physically cannot touch the parts outside its scope cannot break them, no matter what it gets wrong.

## How an agent is defined

In Claude Code, an agent is one small file. It has:

- a **name**
- a **description** — when it runs and what it does
- a **tools** list — only what its job needs (a reader gets read tools, not write tools)
- a **body** — its one job, its inputs, and its hard list of what it cannot do

That is the whole agent. Small, specific, bounded.

See a real one in `../example/job-application-factory/.claude/agents/researcher.md`. Notice how short it is, and how much of it is spent on what the agent cannot do.

Next: `03-the-chain.md` — how agents connect into a factory.
