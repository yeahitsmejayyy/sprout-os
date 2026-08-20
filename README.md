![Sprout OS — a personal AI operating system made of folders and markdown](cover.png)

# 🌱 Sprout OS

<div align="center">

[![Plant one](https://img.shields.io/badge/plant%20one-sprout--os--site.vercel.app-FF6100?style=flat-square)](https://sprout-os-site.vercel.app/) [![License: MIT](https://img.shields.io/badge/license-MIT-FF6100?style=flat-square)](./LICENSE) [![Security policy](https://img.shields.io/badge/security-policy-FF6100?style=flat-square)](SECURITY.md) [![Dependencies: none](https://img.shields.io/badge/dependencies-none-FF6100?style=flat-square)](#-what-you-get) [![Built with Markdown](https://img.shields.io/badge/built%20with-markdown-FF6100?style=flat-square)](#-the-idea)

</div>

**A personal AI operating system made of nothing but folders and markdown.**

No database. No app. No build step.

Your agent reads the markdown and works with your files directly. That's the whole system.

[**Plant one →**](https://sprout-os-site.vercel.app/) · [**See it →**](#-what-it-looks-like) · [**Get started →**](#-get-started) · [**Auto-boot it →**](#️-make-it-boot-itself) · [**Obsidian →**](#-nice-extra-your-notes-as-a-graph)

---

## 👀 What it looks like

You talk. Files appear.

```
> note this — the Acme call went badly, they want to renegotiate scope

  Saved snapshots/2026-07-20-acme-call.md, linked to [[acme]].

> remember that I always want a written scope before any call with them

  Added to memory/acme.md.

> clean up my notes from last week

  Merged 3 notes about the redesign into memory/redesign.md.
  Two snapshots look stale — want me to drop them?
```

**No commands to learn.** There are no commands.

Folders only appear when something needs to go in them. Your space grows to fit your life:

```
day one                    a few months in
─────────                  ───────────────
sprout/                    sprout/
  index.md                   index.md
  install.md                 constitution.md
                             memory/
                               acme.md
                               health.md
                               redesign.md
                             snapshots/
                               2026-07-20-acme-call.md
                               2026-08-02-hiring-idea.md
                             sessions/
                               2026-08-04-hiring.md
                             projects/
                               website/
                                 website.md
```

> None of that was designed up front. It's all residue of use.

---

## 🚀 Get started

**⏱ Two minutes.** Works with any agent that can read and write files.

### Two ways in

| Path | What you do |
|---|---|
| **[The site →](https://sprout-os-site.vercel.app/)** | No terminal. Pick who you are, answer a handful of questions, download a space with your `constitution.md` already written. |
| **The two files** ↓ | Everything below. Same system — you just run the install interview yourself, in your own agent. |

Either way you end up with the same thing: a folder of markdown your agent reads. The site only
moves the install interview into a browser first.

### 1 · Create your Obsidian vault

Install [Obsidian](https://obsidian.md) (free, no account) → **Create new vault** → name it
`sprout`, pick where it lives, e.g. `~/sprout`.

A vault is just a folder of markdown. That folder *is* your Sprout space — same folder, one thing —
which is how you get the graph for free later, with no plugin, connector, or config.

> 💡 **Don't use Obsidian?** Then `mkdir ~/sprout` and move on. Every step below is identical; you
> just don't get the graph. You can install Obsidian and point it at the folder any time.

### 2 · Drop the two files into the vault root

`index.md` and `install.md` are the entire system. They go at the **top level of the vault**, not in
a subfolder:

```bash
git clone --depth 1 https://github.com/yeahitsmejayyy/sprout-os.git sprout-os-tmp \
  && mv sprout-os-tmp/sprout/*.md ~/sprout/ \
  && rm -rf sprout-os-tmp
```

Change `~/sprout` to your vault's path. You should end up with:

```
~/sprout/          ← your vault, and your Sprout space
  index.md
  install.md
```

> 💡 No repo, no `.git`, no dependencies — you took two files, not a project. Want it in version
> control later? `git init` it yourself.

### 3 · Open your agent *in that folder* and install

```bash
cd ~/sprout
claude          # or: codex — or open the folder in Cursor / Windsurf / Zed and start a chat
```

Then say:

> **read install.md**

No agent CLI? Paste the contents of `install.md` into any chat that can write files for you.

### 4 · Answer four short questions

Who you are · how you like to work · anything you won't compromise on · whether you use Obsidian
(say yes — you just made a vault).

A sentence each is plenty. The agent writes your `constitution.md`, then stops.

**That's the install.**

### 5 · Start using it

Every session begins with:

> **read the index**

Then just talk: *"note this"* · *"remember this"* · *"clean up my notes."*

Open the graph view in Obsidian whenever you want to see what you've built.

---

✅ No accounts. No config. No dependencies. Nothing running in the background.

> 📦 **Want Sprout inside a code repo instead?** Put the two files in `your-repo/sprout/` and run
> your agent from the repo root — say *"read sprout/install.md"*, and point Obsidian at the
> `sprout` folder rather than the repo. Most people start with a space of its own and add this
> later, when a project gets big enough to want its own memory.

> 💡 **Already have a folder full of notes?** Copy `index.md` and `install.md` into its root and
> start at step 3. The space is wherever `index.md` lands.

---

## ♾️ Make it boot itself

Every agent autoloads an instructions file when a session starts. Paste this into one, change the
two paths, and Sprout is part of every boot:

```markdown
## Sprout — boot procedure

My Sprout space lives at `~/sprout`. It is an Obsidian vault: folders and markdown, nothing else.

At the start of every session, before you do anything else, read `~/sprout/index.md`.
It defines how this space works — capture conventions, file naming, linking, guardrails.
Follow it exactly for the rest of the session, and re-read it if you lose the thread.

This is not optional and I should not have to ask for it.
```

Two things in it are yours: the **space root** (`~/sprout`) and the **full path to its index**
(`~/sprout/index.md`). Change both together if your folder lives elsewhere — e.g.
`~/work/repo/sprout` and `~/work/repo/sprout/index.md`. Keep them absolute so they resolve from any
directory.

**Where to paste it:**

| Agent | Global — every session, anywhere | Only when you're in the folder |
|---|---|---|
| **Claude Code** | `~/.claude/CLAUDE.md` | `CLAUDE.md` |
| **Codex CLI** | `~/.codex/AGENTS.md` | `AGENTS.md` |
| **Hermes** | your Hermes config, or per-repo → | `.hermes.md`, else `AGENTS.md`, else `CLAUDE.md` |
| **OpenClaw** | `AGENTS.md` in `~/.openclaw/workspace` | `AGENTS.md` in that workspace |

Global is right if Sprout is genuinely your OS. The folder-local file loads only inside the space,
where `index.md` sits right there — so you can drop the paths and just say *"This folder is a
Sprout space. Read `index.md` before doing anything."*

> ⚠️ These files usually already have your own instructions in them. **Append, don't overwrite.**

Or have your agent do it: *"add Sprout to your boot instructions so you always read the index."*

---

## 💡 The idea

One insight runs the whole thing:

> **Markdown plus an AI agent is already enough.**
>
> The agent makes its own folders and files — so you don't design a structure up front. It grows
> as you use it.

It's just text and folders. Every computer already has those.

Nothing to keep running. Nothing to maintain. Nothing to break.

---

## 📄 What you get

Two files, sitting in the root of your vault:

| File | What it does |
|---|---|
| `install.md` | Interviews you once, writes your `constitution.md`, steps aside. |
| `index.md` | The instructions your agent follows. Same for everyone. |
| `constitution.md` | **You.** Your preferences and context. You generate this — you don't download it. |

Everything else — `memory/`, `snapshots/`, `sessions/`, `projects/` — grows inside that same
folder as you use it. Plant a sprout, it grows.

---

## 💬 How you use it

Everything is conversation.

### Capturing — putting things in

| You say | What happens |
|---|---|
| *"note this"* / *"snapshot this"* | dated, immutable note → `snapshots/` |
| *"remember this"* | durable fact → appended to a topic in `memory/` |
| *"log today"* / *"wrap the session"* | session summary → `sessions/` |
| *"start a project called X"* | `projects/x/` appears, with whatever the work needs |

You never say where things go. The agent knows the conventions and picks.

If it's genuinely ambiguous, it asks — rather than inventing a new folder.

### Tending — keeping it clean

> *"clean up my notes"* · *"tidy memory"* · *"merge these two notes"*
> *"what's stale in here?"* · *"prune anything older than March"*

The agent merges duplicates, drops what's dead, and **shows you before deleting** anything you
might want.

⚠️ Nothing runs on a schedule. Maintenance happens when you ask, and only then.

### Finding — getting things back

> *"what did I say about the client last month?"* · *"pull up everything on my health"*
> *"summarize the last two weeks"*

It's plain text. Asking is enough.

---

## 🔧 You can change Sprout by talking to it

This is the part people miss.

`index.md` isn't a config file. `constitution.md` isn't locked after install. They're markdown,
and your agent writes markdown.

**Changing how Sprout behaves is just another conversation.**

> *"be more thorough, the short answers are losing detail"*
> *"stop asking before you delete stuff in `snapshots/` — just do it"*
> *"from now on, dated notes go in `daily/`, not `snapshots/`"*
> *"never write anything about work into my personal memory"*
> *"I want a `reading/` convention for books, one file per book"*

Ask for the change. The agent edits the right file and tells you which:

| File | Holds |
|---|---|
| `constitution.md` | **You** — tone, preferences, hard lines |
| `index.md` | **The system** — conventions, folder rules, capture behavior |

Say *"show me what you changed"* to see the diff.

### Two habits worth having

**1. Correct it in the moment.**
When it does something you don't like, say so right there: *"don't do that again — write it
down."* That's how your constitution grows teeth instead of staying the install-day sketch.

**2. Ask it to explain itself.**
*"Why did you file that there?"* Bad rule → fix the rule. No rule → that's a gap, have it write
one.

### The one guardrail

Sprout's prime directive is **build almost nothing.**

Ask for something that needs real machinery — a script, a database, a sync daemon — and the agent
is instructed to name that out loud and stop, rather than quietly building it.

You can overrule it. It just won't drift there on its own.

---

## 🕸️ Nice extra: your notes as a graph

A Sprout space **is** an [Obsidian](https://obsidian.md) vault.

Not connected to one. Not synced with one. A vault is just a folder of markdown — so the moment
you point Obsidian at your folder, it's a vault.

❌ No plugin. No connector. No API key. No config.

### Seeing it

If you started with a vault in step 1, you're already done — click the graph icon in the left
ribbon. Otherwise: install [Obsidian](https://obsidian.md), **Open folder as vault**, and pick the
Sprout folder itself, not its parent.

Your existing notes are already nodes — and because the vault is scoped to the Sprout folder, your
graph is only your notes. No repo files, no README, no clutter.

> 📦 Heads up if Sprout lives in a code repo: Obsidian writes its own `sprout/.obsidian/` config
> folder when you open the vault. Harmless — `.gitignore` it if it bothers you.

### What to say to your agent

Obsidian only *reads* the folder. The graph is only as good as the links your agent writes:

| You say | What the agent does |
|---|---|
| *"I'm using Obsidian — start linking my notes"* | turns on `[[wikilink]]` conventions going forward |
| *"link up my existing notes"* | back-fills links across everything already written |
| *"make `health` a hub"* | promotes a topic into a Map of Content others point at |
| *"give the client their own note"* | creates a real node so `[[acme]]` stops being a dead link |
| *"any orphans in here?"* | finds notes that link to nothing, wires them in |
| *"add tags for graph colors"* | adds `#topic` tags — off by default, only if you ask |

> 💡 Skipped the Obsidian question during install? Just say **"I use Obsidian now."**

### How the graph gets its shape

Hub-and-spoke, so you get a relational tree instead of a scatter of dots:

- **Leaves link up** → every snapshot and session links out to the topics, projects, and people it
  touches: `[[health]]`, `[[acme]]`, `[[pj]]`
- **Hubs are the targets** → `memory/<topic>.md` files are the centers everything points at
- **Nodes appear on the second mention** → one reference doesn't earn a note; two does
- **Links go one direction** → Obsidian handles backlinks itself
- **Every filename is unique and readable on its own** → the graph shows you basenames and nothing
  else, so no `notes.md`, no bare dates, and no second file called `index.md`

**Don't use Obsidian?** Nothing changes. Wikilinks are just brackets in a text file.

---

## 🌿 Room to grow

When a project inside your space gets big enough to want its own rules:

> *"give this project its own index"*

The agent writes an index note in that folder, named after the folder — `projects/website/website.md`.
Now it's a Sprout space too, with whatever conventions that work needs, inheriting everything it
doesn't override. (Only the root is ever called `index.md`; naming nested ones after their folder
keeps your graph from filling up with nodes labelled "index.")

*"Read the index"* still works. The nearest one wins.

**That's the entire mechanism for growth.** There isn't a second one.

> If you ever feel like you need more than folders and text, the honest answer is usually:
> *not yet.*

---

*Sprout is text and a conversation. That's the whole idea.*
