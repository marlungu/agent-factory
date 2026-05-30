# Job Application Factory

A small, working example of an AI agent factory you run in Claude Code.

It takes one job posting and one resume, and turns them into a tailored application package — a research summary, a role brief, a tailored resume, a cover letter, and an honest fit evaluation. Five specialist agents do the work. You approve at three points. No agent does another agent's job.

This is built on the same pattern teams use to ship software with Claude Code: split the work across specialists, give each one clean context and a hard boundary, and keep a human in control at the decisions that matter. The job application domain is just an easy way to see the pattern work. Once you understand it here, you can point the same structure at any repetitive multi-step task you do.

> This is the worked example for the framework. To understand the method behind it, read `../../method/` (six short files). To build your own factory from this one, see `../../method/06-build-your-own.md`. This README is how to run the example.

## What's in here

```
job-application-factory/
├── CLAUDE.md                  the shared memory every agent reads
├── .claude/
│   ├── agents/                the five specialist agents
│   │   ├── researcher.md
│   │   ├── brief-writer.md
│   │   ├── resume-tailor.md
│   │   ├── cover-letter-writer.md
│   │   └── evaluator.md
│   └── skills/
│       └── job-application-factory/
│           └── SKILL.md       the orchestrator that runs the chain
├── input/
│   ├── job_description.txt     a sample posting (swap in your own)
│   └── resume.txt              a sample resume (swap in your own)
└── output/                     the agents write their results here
```

## The chain

```
Researcher → Brief Writer → [you approve] → Resume Tailor → [you approve]
   → Cover Letter Writer → Evaluator → [you approve] → done
```

## How to run it

1. Open this folder in Claude Code.
2. The sample input files are already in place, so it runs out of the box. To use your own:
   - **Resume** — drop your resume file into `input/` (`.pdf`, `.docx`, or `.txt` all work; no need to convert it), or paste the text into `input/resume.txt`.
   - **Job posting** — paste the posting text into `input/job_description.txt`. Pasting is the reliable path; most job sites block automated fetching, so a URL may not work.
3. Type:

   ```
   Run the job application factory.
   ```

4. The orchestrator runs each agent in turn and stops at the three gates for your approval. Everything else runs on its own.
5. When it finishes, your package is in its own subfolder under `output/` (for example `output/jordan-rivera/`), built in order. Each run gets its own subfolder, so runs do not overwrite each other.

## The one idea to take away

Each agent has one job, its own clean context, and a list of what it cannot touch. That separation is what makes the output trustworthy — and it is the whole point. Swap the agents and the domain, keep the structure, and you have a factory for whatever work you repeat.