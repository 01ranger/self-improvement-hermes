# self-improvement-hermes

A standalone Hermes skill for routing learnings after corrections, failures, repeated issues, and complex tasks.

It helps decide when to use:
- memory
- session_search
- project-local `.learnings/`
- skill_manage

## Structure

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

## What it does

This skill is not a second memory system.
It is a routing layer for deciding the smallest durable place to keep a learning.

## Included files

- `SKILL.md` — main skill instructions
- `references/decision-tree.md` — routing logic
- `references/examples.md` — concrete examples
- `assets/*.md` — starter templates for `.learnings/`
