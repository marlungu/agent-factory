# CLAUDE.md — Job Application Factory

This file loads automatically every session. It is the shared memory for every agent in this project. Read it before doing anything.

## What this project is

A factory that turns one job posting plus one resume into a tailored application package. The work is split across five specialist agents. A human approves at three points. No agent does another agent's job.

## The chain

```
Researcher  →  Brief Writer  →  [APPROVE]  →  Resume Tailor  →  [APPROVE]  →  Cover Letter Writer  →  Evaluator  →  [APPROVE]  →  done
```

The orchestrator runs the chain. Each agent runs in its own context. Each agent gets only what it needs, passed in directly.

## Files

- `input/job_description.txt` — the posting to apply for
- `input/resume.txt` — the candidate's current resume
- `output/` — every agent writes its result here as a separate file

## The output files, in order

1. `output/1-research.md` — extracted requirements and signals
2. `output/2-brief.md` — what this role actually needs
3. `output/3-resume-tailored.md` — the rewritten resume
4. `output/4-cover-letter.md` — the cover letter
5. `output/5-evaluation.md` — fit score and go/no-go

## Hard rules for every agent

- Never invent experience, skills, employers, dates, or numbers. If the resume does not contain it, it does not exist.
- Never claim a degree, certification, or clearance the resume does not state.
- Read your inputs fully before producing anything.
- Stay inside your one job. Do not do the next agent's work.
- If something you need is missing or unclear, say so plainly. Do not guess.
- Write in plain, direct language. No filler, no hype, no marketing tone.

## The three human checkpoints

1. After the Brief Writer — approve the read on the role before any rewriting starts.
2. After the Resume Tailor — approve the tailored resume before the cover letter is written.
3. After the Evaluator — review the fit score before the package is final.

The point of the gates: catch a wrong direction early, before it spreads through every downstream file.
