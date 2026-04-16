# Examples

Each example shows the smallest durable target that fits.

## Example 1: User corrects communication preference

Situation:
- User says: "以后回答再简洁一点。"

Route:
- `memory`

Why:
- This is a stable communication preference that will matter in future sessions.

## Example 2: User references a previous discussion

Situation:
- User says: "上次我们不是处理过这个支付问题吗？"

Route:
- `session_search`

Why:
- The next step depends on past context that likely already exists in history.

## Example 3: Repo-specific build failure

Situation:
- A particular repo only builds after a non-obvious environment variable is set.

Route:
- `.learnings/ERRORS.md`

Why:
- Useful in the current project, but not necessarily a stable cross-session user fact.

## Example 4: Better local workflow discovered

Situation:
- You learn that a recurring local task is safest when run in a particular sequence.

Route:
- `.learnings/LEARNINGS.md`
- If repeated across projects, later promote with `skill_manage`

Why:
- Start local, then promote only after reuse is proven.

## Example 5: Missing capability request

Situation:
- User asks for a capability Hermes does not yet support in the current workflow.

Route:
- `.learnings/FEATURE_REQUESTS.md`

Why:
- This is a candidate for future product or workflow work, not immediate memory.

## Example 6: Reusable debugging workflow

Situation:
- A tricky failure required a specific sequence of inspection, commands, and checks that will likely recur.

Route:
- `skill_manage`

Why:
- The lesson is procedural, repeatable, and expensive to rediscover.

## Example 7: Temporary task progress

Situation:
- "今天先做到这里，明天继续。"

Route:
- Do not write to `memory`
- Keep it in current task context only, unless the user explicitly wants a saved note elsewhere

Why:
- Temporary progress is not durable memory.

## Example 8: Repeated failure pattern

Situation:
- The same class of issue appears for the third time.

Route:
- Stop treating it as isolated
- If it is user- or environment-stable, consider `memory`
- If it is a repeatable workflow, consider `skill_manage`
- If it is still mainly repo-local, keep the evidence in `.learnings/`
- Only consider future default guidance if the rule is broad and low-noise

Why:
- Repetition is evidence that the problem should move up a layer.

## Example 9: Correction that is not global user memory

Situation:
- While working in one repo, the user says: "这个项目里不要跑全量测试，只跑对应模块。"

Route:
- `.learnings/LEARNINGS.md`
- Do not immediately write to `memory`

Why:
- This is a project-local workflow constraint, not necessarily a global user preference.

## Example 10: Prior context beats re-saving

Situation:
- You suspect a similar issue was already solved in an earlier session, but no stable rule has been promoted yet.

Route:
- `session_search` first
- Only save a new durable artifact if the retrieved history reveals a stable pattern worth promoting

Why:
- Retrieval is often cheaper and cleaner than creating duplicate memory.
