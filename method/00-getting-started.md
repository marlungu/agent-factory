# 00 · Getting Started

Start here if you have never used Claude Code. By the end you will have it installed, signed in, and ready to run the example factory. About 15 minutes.

If you already have Claude Code working, skip to `01-the-problem.md` to learn the method, or go straight to the example's README to run it.

---

## What you need

- A computer running **macOS or Windows**. (On Linux, the desktop app is not available — see the CLI note at the bottom.)
- A **paid Claude plan** (Pro, Max, Team, or Enterprise). Claude Code is not on the free plan. You can subscribe at claude.com/pricing.

That is it. The desktop app includes everything else. You do not need to install Node.js, a terminal, or anything separately.

---

## Step 1 · Download and install the app

Go to **claude.com/download** and get the installer for your system:

- **macOS** — the universal build works on both Intel and Apple Silicon.
- **Windows** — the x64 installer for most machines, or the ARM64 installer if you have an ARM device.

Run the installer. Then launch Claude from your Applications folder (macOS) or Start menu (Windows).

> See this: the Claude app opens.

---

## Step 2 · Sign in

Sign in with your Anthropic account.

> See this: the app's main window, with tabs across the top.

There are three tabs:

- **Chat** — plain conversation, no file access. Not what we use.
- **Cowork** — a background agent that works on its own. Not what we use.
- **Code** — an assistant with direct access to your files. **This is the one the factory runs in.**

---

## Step 3 · Open the Code tab

Click **Code** at the top center.

> See this: the Code workspace.

If clicking Code asks you to upgrade, you are on the free plan and need a paid subscription first. If it asks you to sign in online, do that and restart the app.

**Windows users:** you need Git installed for local sessions to work. Get it at git-scm.com/downloads/win. Most Macs already have Git.

---

## Step 4 · Get the framework onto your machine

Download this repo (`agent-factory`) and unzip it somewhere you can find — your Desktop is fine.

Inside it, the runnable factory is at:

```
agent-factory/example/job-application-factory/
```

That is the folder you will open in the next step.

---

## Step 5 · Open the factory as your project

In the Code tab:

1. Choose **Local** (run on your own machine, using your own files).
2. Click **Select folder**.
3. Choose `agent-factory/example/job-application-factory/`.

> See this: a session opens on that folder. `CLAUDE.md` loads automatically — that is the factory's shared memory. The five agents load from the `.claude/` folder inside it.

Pick a model from the dropdown next to the send button if asked. Any current model is fine for this.

---

## Step 6 · Confirm the agents loaded

In the prompt box, type:

```
/agents
```

> See this: five agents listed — researcher, brief-writer, resume-tailor, cover-letter-writer, evaluator.

If you see none, the folder may have been opened before the files were in place. Close the session, reopen the same folder, and try again. Agents load when a session starts.

---

## You're ready

Claude Code is installed and the factory is open in front of you. One thing to know before you run it: by default, Claude **proposes** each change and waits for you to approve it. That is exactly how the factory is meant to work — you stay in control at every step.

Now follow the example's README to run the factory end to end. It will turn a sample job posting and resume into a tailored application package, stopping for your approval at three points.

---

## If you are on Linux, or prefer the terminal

The desktop app is macOS and Windows only. On Linux, or if you would rather work in a terminal, install the Claude Code CLI instead — see the official guide at code.claude.com/docs (Get started with the CLI). The CLI can authenticate with a paid plan or with an API key from console.anthropic.com. Everything in this framework works the same way once `claude` runs in your project folder.

Next: `01-the-problem.md` — why one chat doing everything fails, and what to do instead.
