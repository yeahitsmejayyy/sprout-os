# index: how this space works

You are an agent working inside a Sprout space. This file is your **manual**, not a table of
contents. Read it and you know how to operate here. The folders this file mentions are
*consequences* of the conventions below; they do not exist until work puts something in them.

## Boot

1. Read `constitution.md` in this folder if it exists. That is who I am and how I like to work.
   Everything you do here answers to it.
2. Then read this file. Now you know the conventions. You're booted.

That's the whole startup. There is no database, no index to rebuild, no state to load. This
directory *is* the system.

## Prime directive

**Build almost nothing. Let usage accrete structure.**

- The substrate is only folders and markdown. If something seems to need more than that, say so
  and stop; don't reach for infrastructure.
- **Never pre-create folders or scaffolding.** A folder appears the first time real work needs to
  put a file in it, and not one moment before. An empty `projects/` folder is a smell.
- When you're tempted to add machinery (a script, an index, a manifest, a "system"), that's the
  failure mode this space exists to avoid. Name the felt limitation out loud first; only then
  consider the smallest possible response.

## Capture loop: the core behavior

When I say something like **"note this," "snapshot this," "remember this," "log this"**, you
write markdown to the filesystem, following these conventions. Create the target folder if it
doesn't exist yet.

| I say | You write | Where |
|---|---|---|
| "note this" / "snapshot" / "capture" | a dated point-in-time note | `snapshots/YYYY-MM-DD-slug.md` |
| "remember this" | a durable fact, appended | `memory/<topic>.md` |
| "wrap the session" / "log today" | a session summary | `sessions/YYYY-MM-DD.md` |
| project work | files for that project | `projects/<name>/` |

Conventions:
- **Naming:** date-prefixed where the note is time-bound (`2026-07-19-slug.md`), plain topic
  names where it's durable (`memory/health.md`). Slugs are kebab-case, short.
- **Snapshots** are immutable moments: one file per capture; don't overwrite.
- **Memory** is durable and additive: append to the right topic file, or start a new topic file
  if none fits. Keep entries dated inside the file.
- Every captured file starts with a short front line: a title and the date, so it's legible on
  its own.
- If it's ambiguous where something goes, ask (briefly) rather than guessing a new structure
  into existence.

## Tending

Maintenance is conversation, not mechanism.
- "clean this up," "tidy memory," "prune" mean you read the relevant files, merge duplicates, drop
  what's stale, tighten what's kept. Show me before deleting anything I might want.
- Never run a background process or a scheduled job to do this. It happens when I ask.

## Obsidian graph

A Sprout space *is* an Obsidian vault the moment you open the folder in Obsidian, with no connector,
no config, no separate step. The markdown you're already writing becomes nodes; the links between
notes become the graph. Write files with plain filesystem tools (not any Obsidian plugin/API) so
this stays portable; Obsidian only ever *reads* the folder.

Your one job is to link notes so the graph is a **relational tree, not a scatter of dots**. Use
`[[wikilinks]]` and follow hub-and-spoke:

- **Leaves link up.** Every snapshot and session links to the topics, projects, and people it
  touches: `[[health]]`, `[[sprout]]`, `[[PJ]]`. A leaf that links to nothing is an orphan node,
  so avoid it.
- **Hubs are the targets.** Durable `memory/<topic>.md` notes are Maps of Content: the things
  many leaves point at. They're what gives the graph its centers.
- **Entities become nodes lazily.** The *second* time a person or project is referenced, give it
  its own note (`memory/sprout.md`, `people/pj.md`) so `[[sprout]]` resolves to a real node.
  Never pre-create these; one reference doesn't earn a node.
- **Link one direction only.** Obsidian backlinks are automatic, so leaf→hub is enough; the tree
  shape falls out. Don't hand-maintain reverse links.
- Wikilinks resolve by basename across the vault (`[[health]]` finds `memory/health.md`), so keep
  hub/entity filenames short and unique. Date-prefixed leaf files are fine: they link out, they
  rarely get linked to.

Optional polish, only if I ask: tags (`#topic`) for graph coloring/filtering. Don't add them by
default.

## Fractal property

Any folder can be its own Sprout space by holding an `index.md`. "Read the index" works at any
depth. When a project grows enough to deserve its own conventions, give it an `index.md`; don't
build anything special for this; it already works.
