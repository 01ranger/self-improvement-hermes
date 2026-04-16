# self-improvement-hermes

A standalone Hermes skill for routing learnings after corrections, failures, repeated issues, and complex tasks.

It helps Hermes choose the smallest durable place to keep a learning:
- `memory`
- `session_search`
- project-local `.learnings/`
- `skill_manage`

## Why this skill exists

Hermes already has memory, session recall, and skill creation.

What it often needs is a cleaner decision layer:
- when to save something
- where to save it
- when not to save it
- when a repeated issue should be promoted into a reusable workflow

This skill provides that routing logic.

## What’s included

```text
self-improvement-hermes/
├── SKILL.md
├── references/
│   ├── decision-tree.md
│   └── examples.md
└── assets/
    ├── LEARNINGS.md
    ├── ERRORS.md
    └── FEATURE_REQUESTS.md
```

## Core routing model

- Stable cross-session fact or preference -> `memory`
- Prior-chat context that should be recalled -> `session_search`
- Project-local lesson or failure -> `.learnings/`
- Reusable workflow -> `skill_manage`
- One-off detail -> keep it local to the current task

## Install

Copy the `self-improvement-hermes/` directory into your Hermes skills directory:

```bash
mkdir -p ~/.hermes/skills/software-development
cp -r self-improvement-hermes ~/.hermes/skills/software-development/
```

Then load it in Hermes as:

```text
software-development/self-improvement-hermes
```

## When to use it

Use this skill when:
- the user corrects Hermes
- a tool call or command fails
- a similar issue happens again
- Hermes realizes its knowledge was outdated
- a complex task finishes and may be worth promoting into a reusable skill

## Included files

- `SKILL.md` — main instructions
- `references/decision-tree.md` — routing logic
- `references/examples.md` — concrete examples
- `assets/*.md` — starter templates for `.learnings/`

## Design principles

- Prefer the smallest durable layer that prevents future rework
- Do not turn temporary task state into memory
- Do not create `.learnings/` everywhere by default
- Promote only proven, reusable workflows into skills
- Use retrieval before creating duplicate durable storage

## License

MIT
