# install: read me first

You (the agent) are installing Sprout for the human reading this with you. Sprout is a personal
OS whose entire substrate is folders and markdown, nothing else. Your job here is small: **a
short interview, then write one file.**

Do not build anything. Do not create folders. Installing Sprout produces exactly one new file:
`constitution.md`. `index.md`, the machine, already ships in this folder, untouched.

## What you're producing

`constitution.md` = **who this person is and how they like to work.** It's theirs, it's short, and
it grows over time. You're capturing a *seed*, not an essay. A sentence per answer is plenty.

## The interview

Ask these one at a time, conversationally, and keep *your own* questions short. Don't interrogate,
don't pad. If they give you a word, take the word; depth accrues later through use.

1. **What's this space for, and who are you in it?** (A line of context, like "my personal life
   OS," "my consulting work," whatever it is.)
2. **How do you want me to work with you?** (Any standing preferences on tone or manner. The
   default is already *concise, honest over comfortable, push back on scope creep*; they can just
   say "that's fine" or adjust it.)
3. **Anything you care about or won't compromise?** (Optional values or hard lines. Fine to skip.)
4. **Do you use Obsidian?** If this folder is already a vault, that's a yes — don't make them
   answer twice. If yes, they get the relational graph for free; `index.md` already explains the
   `[[wikilink]]` and filename conventions, so just note it's on. If no, nothing changes; the
   Obsidian section simply sits unused (the filename rules still apply either way).

## Writing the file

From their answers, write `constitution.md` in *their* register, not corporate boilerplate. Keep
the shape light: a "Working with me" section, a "Who I am" section, and a "Values" section that
can be a stub if they skipped question 3. Leave clear room for it to grow. Show it to them before
you're done; let them edit a line.

**Default the "Working with me" section to concise** unless they asked for something else: lead
with the answer, skip filler, expand only when asked. Write this into the file as the standing
default, and note in it that they can change it anytime (e.g. "be more thorough"). Concise is
where it starts, not a cage.

## Finishing

Once `constitution.md` exists and they're happy with it:

1. Tell them Sprout is installed.
2. Tell them how to start: **"Read the index."** That boots the space. From then on it's plain
   conversation: "note this," "remember this," "clean this up."
3. Offer, in one line, to wire up auto-boot so they never have to say "read the index": a short
   pointer added to their agent's instructions file naming the space's absolute root and the full
   path to `index.md` (globally in e.g. `~/.claude/CLAUDE.md` or `~/.codex/AGENTS.md`, or locally
   in a `CLAUDE.md`/`AGENTS.md` beside `index.md`). **Append, never overwrite** — read the file
   first. Only do this if they say yes.
4. This file has done its job. Offer to delete `install.md`, or leave it; their call.

That's the whole install. No database, no dependencies, no build step. Text and a conversation.
