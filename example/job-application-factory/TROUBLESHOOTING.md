# Troubleshooting · Permission and Access Issues

If the factory will not read its input files or write to `output/`, the cause is almost always Claude Code's permission system — not the files themselves. There are three distinct situations. Find yours and apply the fix.

---

## Quick diagnosis

Run this in your terminal (not in Claude):

```
ls -la /path/to/job-application-factory/input/
```

- **You see `job_description.txt` and `resume.txt`** → the folder is fine. The block is in Claude Code's permissions. Go to Situation 1 or 3.
- **You get `permission denied`** → it could be a sandbox blocking the shell too. Go to Situation 3.

---

## Situation 1 · Claude asks permission and you said "yes" in the chat

**What you see:** Claude says something like "I'm hitting permission restrictions on the input/ directory. Could you allow read access?"

**Why:** Claude Code gates file access at the settings level. Typing "yes" in the chat does **not** grant it — the permission system does not read your chat reply as a config change.

**Fix:** This factory ships with a `.claude/settings.json` that pre-grants read access to the project and write access to `output/`. If you still get asked, reply:

```
Use update-config to grant read and write access to this project directory.
```

That grants it properly, then the chain continues.

---

## Situation 2 · Fresh machine, no prior Claude Code setup

**What you see:** It just works. The factory's own `.claude/settings.json` clears the path and you are not stopped for file access.

**Nothing to fix.** This is the normal experience for someone using Claude Code for the first time. The settings file does its job.

---

## Situation 3 · You have a global sandbox or workspace lockdown from earlier work

**What you see:** Claude says the directory is "blocked by your current permission settings — both for me and for subagents," and that it cannot even read its own config to fix it. A plain `ls` in your terminal may also be denied if the sandbox is strict.

**Why:** If you have previously configured Claude Code with a sandbox, deny rules, or a workspace-scoped restriction (for example, locking it to one folder like `~/workspace`), that config is **global**. It sits above any project's settings and denies first — by design, so no single project can disable your safety net. The factory's own `.claude/settings.json` cannot override it. And Claude inside that session cannot reach the global config to fix it.

**Fix — add the factory to your global allowed directories.** Paste this into the Claude Code prompt and press Enter. Change `target` to your actual factory path first:

```
! python3 -c "
import json, os
p = os.path.expanduser('~/.claude/settings.json')
try:
    with open(p) as f: d = json.load(f)
except FileNotFoundError: d = {}
perms = d.setdefault('permissions', {})
dirs = perms.setdefault('additionalDirectories', [])
target = '/Users/YOURNAME/path/to/job-application-factory'
if target not in dirs:
    dirs.append(target)
with open(p, 'w') as f: json.dump(d, f, indent=2)
print('Done — restart Claude Code for changes to take effect')
"
```

Then **quit Claude Code completely and reopen it** — the global config loads at startup, so a soft restart will not pick it up. Reopen the factory folder and say "Continue running the factory."

**Alternative:** move the factory out of the locked workspace. Copy the whole `ai-work-os` folder somewhere outside the restricted path (your Desktop, for example) and open the factory from there. Outside the lockdown, the project's own settings file takes over and it runs cleanly.

---

## For running a workshop

These three situations map directly onto the people in the room:

- **Most attendees are Situation 2** — first-time users, nothing configured, the factory just runs.
- **Situation 1** is the one everyone might briefly see — the "yes in chat does not work" trap. Warn them once up front.
- **Situation 3** hits the technical attendees who have used and locked down Claude Code before. Have the one-liner above ready to hand them.

A clean way to avoid Situation 3 entirely: have attendees place the workshop folder somewhere neutral (Desktop or Documents), not inside any folder they have previously restricted.

One more note on getting the folder onto a machine: a `git clone` preserves file permissions cleanly, while an unzipped download can occasionally arrive with odd permissions. If you are distributing the framework for a workshop, a clone is the more predictable path.
