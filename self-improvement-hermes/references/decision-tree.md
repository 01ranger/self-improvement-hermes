# Decision Tree

Use this file when the main skill needs a sharper routing decision.

## Step 1: Is it globally durable?

Promote to `memory` if all are true:

- it will still matter in future sessions
- it helps avoid future user correction or re-explanation
- it is about the user, the environment, or a stable convention

If it is only about the current task or repo, do not default to memory.

## Step 2: Is prior context the real need?

Use `session_search` if the user says or implies:

- we did this before
- last time
- as mentioned earlier
- remember when
- you already helped with this

Try retrieval before asking the user to restate prior work.

## Step 3: Is it project-local?

Use `.learnings/` if the information is useful in the current codebase but not broadly durable enough for memory.

Typical examples:

- a local build gotcha
- a repo-specific deployment sequence
- a flaky integration detail
- a failure pattern in the current workspace

Do not default to `.learnings/` when the information is really:

- a stable user preference -> use `memory`
- a reusable multi-project workflow -> use `skill_manage`
- a hint that prior session context exists -> use `session_search`

## Step 4: Is it reusable as procedure?

Promote to a skill when the lesson has:

- repeatable triggers
- repeatable steps
- explicit pitfalls
- a way to verify success

If it still depends heavily on the original conversation, keep refining it in `.learnings/` first.

## Step 5: Does it deserve top-level rule status?

Only elevate a rule into core agent guidance when:

- it appears across multiple tasks
- it remains valid over time
- it adds little prompt noise
- it guides an important default action

Examples of good core-rule candidates:

- user corrections should trigger memory judgment
- historical references should trigger session recall
- complex tasks should trigger skill-promotion judgment

Examples of bad core-rule candidates:

- project-specific shell flags
- one repo's local port number
- a single API quirk from one integration

## What not to record by default

Avoid storing the following unless the user explicitly wants them captured:

- secrets and private credentials
- raw terminal logs with sensitive data
- full config files
- every completed step of a task
- emotional narration or diary-style commentary

## Heuristic for repeated problems

- once: fix and move on
- twice: note the pattern
- three times: stop treating it as isolated; evaluate memory, skill, or rule promotion
