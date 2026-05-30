# Agent Factory

A framework for orchestrating AI agents to do real, multi-step work — reliably, with you in control.

Most people use AI as one chat that does everything at once: research it, plan it, build it, check it, all in the same window. It feels fast and falls apart slowly. Mistakes made early hide in the noise and spread. By the end you are supervising a mess you cannot see clearly.

This framework teaches a different way: split the work across **specialist agents**, give each one a single job and a clean workspace, set hard rules about what each cannot touch, and keep a human at the few decisions that matter. The result is a **factory** — a chain of agents that does the whole job while you stay in control of the direction.

You do not need to be a developer to learn this. You need Claude Code and a willingness to build one small thing.

## What this repo is

Two parts: the **method** (the framework — how to orchestrate agents) and one **example** (a working factory you can run today).

```
agent-factory/
├── README.md                     you are here
├── method/                       THE FRAMEWORK — how to orchestrate agents
│   ├── 00-getting-started.md     install Claude Code, sign in, open the factory
│   ├── 01-the-problem.md         why one chat doing everything fails
│   ├── 02-the-agent.md           one job, clean context, hard boundary
│   ├── 03-the-chain.md           research → plan → build → verify → validate
│   ├── 04-human-gates.md         where you stay in control
│   ├── 05-memory.md              the rules that survive every session
│   └── 06-build-your-own.md      turn the method into your own factory
└── example/
    └── job-application-factory/  a complete, runnable factory
        ├── README.md             what it is and how to run it
        └── ...                   five agents, an orchestrator, sample inputs
```

## How to use it

**If you have never used Claude Code:** start with `method/00-getting-started.md`. It takes you from nothing to the factory open on your screen in about 15 minutes.

**To learn the method:** read `method/` in order, from `01-the-problem.md`. Six short files after setup. No theory you cannot act on. By the end you understand how to orchestrate agents.

**To see it work:** run `example/job-application-factory/`. Its README walks you through it in under an hour. You will watch the method run.

**To build your own:** `method/06-build-your-own.md` shows you how to point the same structure at whatever you repeat in your own work.

## The method in one paragraph

A factory is a chain of specialist agents. Each agent has **one job**, its **own clean context**, and a **hard boundary** of what it cannot touch. They run in a fixed order — research, then plan, then build, then verify, then validate. A **human approves** at the few points where a wrong direction would be expensive to discover late. A shared memory file holds the rules every agent follows and **learns** from every mistake. Keep those pieces, change everything else, and you have a factory for any repetitive multi-step work.

## The one thing to remember

One job per agent. Clean context. A hard boundary. A human at the gates. A memory that learns.

That is the whole framework. The rest is detail.
