# skill-handoff

Compact the current conversation into a handoff document for another agent to pick up.

## Intro

`handoff` writes a concise document summarising the current conversation so a fresh agent can continue where the current one left off. It avoids duplicating content already captured in other artifacts (PRDs, plans, commits, diffs) — referencing them by path or URL instead. When arguments are provided, they describe what the next session will focus on, and the document is tailored accordingly.

## How it works

The skill creates a temp file with `mktemp -t handoff-XXXXXX.md`, reads it before writing, then fills it with a compact summary of the conversation state. It also suggests any skills the next session should use based on what was in progress.

## Usage

```
/handoff [what the next session will be used for]
```

Pass an optional argument describing the next session's focus. The skill produces a Markdown file at a temp path and prints the path so you can reference or share it.

## Files in this repo

| File | Purpose |
|------|---------|
| `SKILL.md` | Skill definition and instructions |

## Install

Clone this repo into a `claude-skills` library under `skills/handoff/`, then run the library's sync step to publish the `/handoff` command.
