---
name: self-improvement-hermes
description: Hermes-native self-improvement workflow. Use when deciding whether a correction, failure, repeated issue, or completed complex task should be routed to memory, session_search, skill_manage, or project-local .learnings files.
version: 1.0.0
author: Hermes Agent
license: MIT
metadata:
  hermes:
    tags: [self-improvement, memory, reflection, workflow, learnings]
    related_skills: [systematic-debugging, test-driven-development, writing-plans]
---

# Self-Improvement for Hermes

Use this skill to route learnings after a correction, failure, repeated issue, or non-trivial task.

This is not a second memory system. It is a routing layer for Hermes' existing capabilities.

## One-Line Routing Map

- Stable cross-session fact or preference -> `memory`
- Prior-chat context you should retrieve -> `session_search`
- Project-local lesson or failure -> `.learnings/`
- Reusable workflow -> `skill_manage`
- One-off detail -> keep it local to the current task

## When to Use

Use this skill when any of these happen:

1. The user corrects you
2. A tool call, command, or integration fails unexpectedly
3. You discover your understanding was outdated or incomplete
4. A similar problem appears again
5. You finish a complex task, tricky bugfix, or non-trivial workflow
6. You are unsure whether something belongs in memory, a skill, or only local notes

## Fast Routing Rules

### `memory`

Use `memory` for:

- Stable user preference, habit, or constraint
- Durable environment or workflow fact
- Anything whose loss would likely cause future correction

Do not use `memory` for:

- Temporary task state
- Completed-work logs
- Long project diaries
- One-off debugging details

### `session_search`

Use `session_search` when:

- The user references prior work or earlier discussion
- Relevant context likely exists in history
- The next step depends on what happened before

If the conversation implies prior context exists, do not guess first.

### `.learnings/`

Use project-local `.learnings/` when:

- The issue is mainly local to the repo, workspace, or task
- The lesson is worth keeping but not durable enough for `memory`
- You want evidence for later promotion to a skill or rule

### `skill_manage`

Use `skill_manage` when the lesson is:

- Reusable across tasks or projects
- Concrete enough to teach as a workflow
- Verified through use
- Expensive to rediscover repeatedly

### Future agent guidance

A learning is a candidate for default agent guidance only if it is:

- High-signal across many tasks
- Stable over time
- Low-noise in the top-level prompt
- About Hermes' general operating method

## Routing Decision Tree

Use this order:

1. Stable cross-session fact or preference? -> `memory`
2. Prior session context should be recalled? -> `session_search`
3. Project-local lesson, error, or gap? -> `.learnings/`
4. Reusable workflow with triggers and verification? -> `skill_manage`
5. None of the above? -> keep it local to the current task

For more detail, see `references/decision-tree.md`.

## `.learnings/` Directory

Create `.learnings/` only when it is actually useful for the current project.

Suggested structure:

```text
.learnings/
├── LEARNINGS.md
├── ERRORS.md
└── FEATURE_REQUESTS.md
```

Rules:

- Create missing files only; do not overwrite existing content
- Prefer concise summaries over raw logs
- Never store secrets, tokens, private keys, or full sensitive configs by default
- Treat these files as project-local working memory, not as a second global memory system

## Three Log Types

### `LEARNINGS.md`

Use for:

- User corrections that are project-local rather than user-global
- Outdated knowledge you had to update
- Better approaches discovered during execution
- Insights from post-task reflection

### `ERRORS.md`

Use for:

- Command failures
- Tool or API failures
- Unexpected integration behavior
- Useful failure context that may recur in the same project

### `FEATURE_REQUESTS.md`

Use for:

- Missing capabilities the user asked for
- Repeated local needs that do not yet justify product-level work
- Candidate enhancements to revisit later

## Promotion Rules

Use these thresholds:

- First appearance: log only if it seems useful later
- Second appearance: treat it as a recurring-pattern candidate
- Third appearance: explicitly evaluate promotion to `memory`, `skill_manage`, or future agent guidance

### Promotion Matrix

Use this matrix when deciding what to promote:

| Signal | Best Target | Reason |
|--------|-------------|--------|
| Stable user preference or constraint | `memory` | Prevents repeated correction |
| Missing historical context | `session_search` | Retrieve, don't re-store |
| Project-local failure or lesson | `.learnings/` | Cheap, local, low-noise |
| Proven reusable workflow | `skill_manage` | Expensive to rediscover |
| Broad, stable, low-noise operating rule | future agent guidance | Improves default behavior |

Promote to a skill when the solution is proven, reusable, and cheap to teach.
Promote to top-level agent guidance only when the rule is broadly applicable and low-noise.

### Before You Promote

Ask these questions in order:

1. Is this still useful outside the current task?
2. Would the user likely need to remind or correct Hermes again if this is lost?
3. Is this mainly local to the repo or workspace?
4. Does it describe a repeatable procedure with clear triggers and verification?
5. Would promoting it add signal, or just more noise?

If you cannot clearly answer these, keep the item at the lower layer for now.

## Anti-Patterns

Avoid these mistakes:

- Writing temporary task progress into `memory`
- Turning every bug into a global rule
- Logging every failure automatically without judgment
- Creating `.learnings/` in every repo by default
- Promoting unverified ideas into skills
- Repeating the same fix three times without considering promotion

## Minimal Operating Habit

After a complex task, ask four quick questions:

1. Stable user or environment fact? -> `memory`
2. Prior-chat context I should retrieve next time? -> `session_search`
3. Project-local lesson worth keeping? -> `.learnings/`
4. Reusable workflow worth teaching? -> `skill_manage`

If all four are no, do not force a write.

## Examples

See `references/examples.md` for concrete routing examples.

## Quick Summary

- `memory` for durable cross-session facts
- `session_search` for recalling prior work
- `.learnings/` for project-local lessons and failures
- `skill_manage` for reusable workflows
- Default to the smallest durable layer that prevents future rework
