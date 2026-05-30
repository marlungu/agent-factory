# 05 · Memory

Every time you open a fresh AI session, it starts with no memory of your project. It does not know your rules, your conventions, or the mistakes it made last time. Left alone, it relearns — and re-breaks — the same things every session.

A factory fixes this with one shared file: **CLAUDE.md**.

## What CLAUDE.md is

A plain text file at the root of your factory. Claude Code loads it automatically at the start of every session. Every agent reads it before doing anything.

It holds the permanent facts and rules of your project:

- **What the project is** — the job the factory does, in a sentence or two.
- **The files** — what the inputs are and where outputs go.
- **The chain** — the agents and the order they run in.
- **The hard rules** — what every agent must never do, no matter the domain.
- **The gates** — where the human approves.

Keep it short. A page or two. It is the rules, not a manual.

## Why it matters

Without it, each agent guesses at your project's conventions and gets them wrong in its own way. With it, every agent starts from the same shared understanding. The researcher, the builder, and the checker all follow the same rules because they all read the same file.

## The most important rules are the "never" rules

Of everything in CLAUDE.md, the rules that matter most are the ones that tell an agent what it must **never** do. In the example factory:

- Never invent experience, skills, employers, or dates.
- Never claim a credential the resume does not state.
- Never guess when something is unclear — say so instead.

These are not domain trivia. They are the difference between an AI that flatters you and a system you can trust. An agent with no "never" rules will fill gaps with confident, plausible, wrong work — a resume with a degree the candidate does not have, a number nobody measured. The never rules are what stop that.

And they transfer almost unchanged to any serious domain. "Never claim a credential the resume does not state" is the same discipline as "never record an audit entry the system did not actually produce." A tool that refuses to fabricate is the only kind you can put in front of work that gets reviewed. If you take one thing from this framework into your own factories, take the habit of writing the never rules first.

## How it learns

This is the part that compounds.

Every time an agent makes a mistake that surprises you, ask one question:

> Would a rule in CLAUDE.md have prevented this?

If yes, add the rule. Do not just fix the one instance — fix the source. Add the rule and it never happens again, in any session, for any agent.

Over a few runs, CLAUDE.md becomes a record of every assumption your agents got wrong. The factory gets steadily more reliable without you supervising harder. The knowledge lives in the file, not in your head and not lost when the session ends.

## See it

The example factory's memory is `../example/job-application-factory/CLAUDE.md`. Read it. Notice how much of it is hard rules, and how short the whole thing is.

Next: `06-build-your-own.md` — turn this method into a factory for your own work.
