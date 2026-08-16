# Security

Sprout OS ships two markdown files. There is no code here to run, and nothing that runs on its own.

## What this repo contains

Everything tracked in this repo, in full: `sprout/index.md`, `sprout/install.md`, `README.md`,
`cover.png`, `.gitignore`, and `.claude/settings.json`. No scripts, no dependencies, no build step,
no package manifest.

Check it yourself:

```bash
git ls-files
```

## What it touches

The files are instructions for an *agent*. They don't do anything; your agent does, and only when
you're in a session with it.

What `index.md` tells the agent to do:

- **Write markdown inside your space** — `snapshots/`, `memory/`, `sessions/`, `projects/`, created
  as work needs them, under the folder you opened.
- **Read files in that space** so it can answer questions and tidy notes.
- **Ask before deleting** anything you might want, and **never delete `constitution.md`**.

What it never asks for:

- No network calls, no uploads, no telemetry, no accounts, no API keys.
- No background processes and no scheduled jobs — `index.md` says so outright, under *Tending*.
- Nothing outside your space, with one exception: at the end of the install, `install.md` **offers**
  to append a boot line to your agent's instructions file (`~/.claude/CLAUDE.md`, `AGENTS.md`, or
  similar) and offers to delete itself. Both are opt-in, and both only happen if you say yes.

Every one of those claims is a line in the two files. They're 184 lines total — read them:

```bash
cat sprout/index.md sprout/install.md
```

## The honest caveat

Your agent has whatever access you gave it, not whatever this repo grants. Sprout can't widen that,
and it can't narrow it either. If your agent can reach your whole home directory, it still can while
Sprout is installed — the instructions here just tell it to work inside the space. Scope your agent
the way you'd want it scoped anyway.

And these are *your* files after you install: `index.md` and `constitution.md` are meant to be edited
by talking to the agent. Read what changed when you change them.

## Supported

The two files in `sprout/` on `main`. There are no releases and no versions to patch back to — if
something's wrong, the fix is the current copy of the file.

## Reporting

Open an issue: https://github.com/yeahitsmejayyy/sprout-os/issues

If it's a vulnerability, **say so in the title and leave the details out** until there's a private
channel to send them through.
