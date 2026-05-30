# CLAUDE.md — Job Application Factory

This file loads automatically every session. It is the shared memory for every agent in this project. Read it before doing anything.

## What this project is

A factory that turns one job posting plus one resume into a tailored application package. The work is split across five specialist agents. A human approves at three points. No agent does another agent's job.

## The chain

```
Researcher  →  Brief Writer  →  [APPROVE]  →  Resume Tailor  →  [APPROVE]  →  Cover Letter Writer  →  Evaluator  →  [APPROVE]  →  done
```

The orchestrator runs the chain. Each agent runs in its own context. Each agent gets only what it needs, passed in directly.

## Inputs — two ways to provide them

The factory needs the candidate's resume and the job posting. There is flexibility in how each arrives.

**The resume** can be either:
- A file dropped into `input/` in any common format (`.pdf`, `.docx`, `.txt`). Claude Code reads these directly. This is the easy path — no copy-paste.
- Or pasted text in `input/resume.txt`.

The Researcher looks in `input/` for any resume file first; if it finds one, it uses it. If it finds only `resume.txt` with real content, it uses that.

**The job posting** is pasted directly into the conversation by the user when they start the run. This is the easy path — no file to edit. The orchestrator captures the pasted posting and passes it to the Researcher. (A posting saved in `input/job_description.txt` also works as a fallback, and the sample one ships there so the factory runs out of the box.) If the user gives only a URL, ask them to paste the posting text instead — most job sites block automated fetching, so a URL is unreliable. Never guess at a posting's contents.

## Outputs — one folder per run

Each run writes to its own subfolder inside `output/`, so runs do not overwrite each other.

- The orchestrator picks a short run name (for example, from the candidate's name or the role) and uses `output/<run-name>/`.
- If unsure, ask the user for a run name, or default to `output/run/`.
- All five files for a run go in that run's subfolder.

## The output files, in order (inside the run's subfolder)

1. `1-research.md` — extracted requirements and signals
2. `2-brief.md` — what this role actually needs
3. `3-resume-tailored.md` — the rewritten resume
4. `4-cover-letter.md` — the cover letter
5. `5-evaluation.md` — fit score and go/no-go

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