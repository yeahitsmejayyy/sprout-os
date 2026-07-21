![Sprout OS — a personal AI operating system made of folders and markdown](cover.png)

# 🌱 Sprout OS

**A personal AI operating system made of nothing but folders and markdown.**

No database. No app. No build step.

Your agent reads the markdown and works with your files directly. That's the whole system.

[**See it →**](#-what-it-looks-like) · [**Get started →**](#-get-started) · [**Auto-boot it →**](#️-dont-want-to-say-read-the-index-every-time) · [**Obsidian →**](#-nice-extra-your-notes-as-a-graph)

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
                               2026-08-04.md
                             projects/
                               website/
                                 index.md
```

> None of that was designed up front. It's all residue of use.

---

## 🚀 Get started

**⏱ Two minutes.** Works with any agent that can read and write files.

### 1 · Get the `sprout` folder

That folder — two markdown files — is the whole thing. Grab it and drop it where you want it:

```bash
git clone --depth 1 https://github.com/YOUR-USERNAME/sprout-os.git tmp \
  && mv tmp/sprout ~/sprout \
  && rm -rf tmp
```

Change `~/sprout` to wherever it belongs:

| | Put it | Good for |
|---|---|---|
| 🏠 **A space of its own** | `~/sprout` | Your life OS. Notes, memory, thinking. |
| 📦 **Inside a project** | `your-repo/sprout` | One codebase's memory: decisions, context, what you tried. |

Most people start with 🏠 and add 📦 later, when a project gets big enough to want its own memory.

> 💡 Sprout has no opinion about version control. There's no `.git` to clean up — you took the
> folder, not the repo. Want it in git later? `git init` it yourself. Don't? Works exactly the same.

> 💡 **You're not choosing once.** Any folder with an `index.md` is its own Sprout space. Nest them
> freely — *"read the index"* works at any depth, and the nearest one wins.

### 2 · Open it with your agent

| Your agent | How |
|---|---|
| **Claude Code** | `claude` |
| **Codex CLI** | `codex` |
| **Cursor / Windsurf / Zed** | open the folder, start a chat |
| **Anything else** | paste `install.md` into the chat |

🏠 For a space of its own, `cd ~/sprout` first — then everything below has no paths in it.
📦 Inside a project, stay at the repo root and prefix the paths with `sprout/`.

### 3 · Say this

> **read install.md** &nbsp;·&nbsp; 📦 *in a repo:* **read sprout/install.md**

### 4 · Answer four short questions

Who you are · how you like to work · anything you won't compromise on · whether you use Obsidian.

A sentence each is plenty. The agent writes your `constitution.md`, then stops.

**That's the install.**

### 5 · Start using it

Every session begins with:

> **read the index**

Then just talk: *"note this"* · *"remember this"* · *"clean up my notes."*

---

✅ No accounts. No config. No dependencies. Nothing running in the background.

> 💡 **Already have a folder you want to use?** Copy the `sprout` folder into it and start at
> step 2. Or, if you'd rather it *be* that folder, copy `index.md` and `install.md` in directly —
> the space is wherever `index.md` lands.

---

## ♾️ Don't want to say "read the index" every time?

Every major agent already autoloads an instructions file at session start. Drop **one line** in
it and Sprout boots itself.

**Which file:**

| Agent | Instructions file |
|---|---|
| **Claude Code** | `CLAUDE.md` |
| **Codex CLI** | `AGENTS.md` |
| **Hermes** | `AGENTS.md` (or `.hermes.md` — it checks `.hermes.md` → `AGENTS.md` → `CLAUDE.md`) |
| **OpenClaw** | `AGENTS.md` in your workspace (default `~/.openclaw/workspace`) |

**Where it goes, and what to write** — it depends on where you run your agent from:

🏠 **You work inside the folder** (`cd ~/sprout`). The file goes *in* `sprout/`, right next to
`index.md`. No paths, nothing outside the folder:

```markdown
This folder is a Sprout space. Read `index.md` before doing anything here.
```

📦 **You work at a repo root** and Sprout lives in `sprout/`. The file is your repo's existing one:

```markdown
This repo has a Sprout space at `sprout/`. Read `sprout/index.md` before working in it.
```

Create the file if it isn't there. **If it already exists, add the line — don't replace what's in
it.**

Or just ask: *"wire this up so I don't have to say 'read the index' every time."* The install
agent offers to do exactly this, and it already knows which of the two cases you're in.

### Making Sprout your default, everywhere

Want your space reachable from *any* directory — including while you're working in a code repo?
Put a pointer in the **global** instructions file instead. If you took the default location, this
is copy-paste:

```markdown
My Sprout space is at ~/sprout.
When I say "note this," "remember this," or "read the index,"
read ~/sprout/index.md and follow it.
```

| Agent | Global file |
|---|---|
| **Claude Code** | `~/.claude/CLAUDE.md` |
| **Codex CLI** | `~/.codex/AGENTS.md` |
| **Hermes** | project `AGENTS.md` per repo, or your shell's Hermes config |
| **OpenClaw** | `AGENTS.md` in `~/.openclaw/workspace` (already global) |

> ⚠️ These global files usually already have your own instructions in them. **Append, don't
> overwrite.** Read the file first.

> 💡 This makes Sprout's rules load in *every* session, everywhere. Great if Sprout is genuinely
> your OS. Noisy if you just wanted a notes folder — in that case stick with the per-folder
> version above.

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

One folder, `sprout/`, containing two files:

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

### Getting it connected

1. Install [Obsidian](https://obsidian.md) — free.
2. **Open folder as vault** → pick the `sprout` folder itself, not its parent.
3. Click the graph icon in the left ribbon.

Done. Your existing notes are already nodes — and because the vault is scoped to `sprout/`, your
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

**Don't use Obsidian?** Nothing changes. Wikilinks are just brackets in a text file.

---

## 🌿 Room to grow

When a project inside your space gets big enough to want its own rules:

> *"give this project its own index"*

The agent writes an `index.md` in that folder. Now it's a Sprout space too — with whatever
conventions that work needs, inheriting everything it doesn't override.

*"Read the index"* still works. The nearest one wins.

**That's the entire mechanism for growth.** There isn't a second one.

> If you ever feel like you need more than folders and text, the honest answer is usually:
> *not yet.*

---

*Sprout is text and a conversation. That's the whole idea.*
