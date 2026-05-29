---
name: diff-discipline
description: "Use after any code implementation to verify surgical precision — every changed line must trace to the task. Enforces Karpathy Rule 3 (Surgical Changes) with concrete post-implementation checks."
---

# Diff Discipline

## Overview

LLM agents drift. They "improve" adjacent code, refactor things that aren't broken, and change formatting to match their preferences. This skill catches that drift after implementation, before commit.

**Core principle:** Every changed line must trace directly to the user's request. If it doesn't, revert it.

**This is a RIGID skill.** Follow exactly. Don't adapt away discipline.

## When to Use

- After completing any implementation, before committing
- During code review (self or peer)
- When reviewing subagent output
- Whenever `git diff` shows more files than expected

## The Diff Audit

### Step 1: Review the Diff

Run `git diff --stat` to see what files changed and how many lines.

```bash
git diff --stat
```

### Step 2: Check File Count

```
FILES CHANGED vs FILES IN TASK SPEC

Task mentions 2 files → diff shows 2 files → ✅ Proceed to Step 3
Task mentions 2 files → diff shows 5 files → ❌ STOP

For each extra file:
  - Is this change REQUIRED by the task? (import update, type export)
    YES → Acceptable collateral. Note it.
  - Is this an "improvement" or "cleanup"?
    YES → REVERT. Don't touch it.
  - Is this a formatting/style change?
    YES → REVERT. Match existing style.
```

### Step 3: Line-by-Line Trace

For every changed hunk in the diff, answer:

```
This change: [describe the change]
Required by: [which part of the task spec]
   → If you can't point to a specific requirement → REVERT
```

### Step 4: Style Consistency Check

For every new line of code:

```
Does this match existing style in the file?
  - Naming convention (camelCase vs snake_case)
  - Indentation (tabs vs spaces, 2 vs 4)
  - String quotes (single vs double)
  - Import style (named vs default)
  - Comment style (// vs /* */)
  - Error handling pattern

Mismatch found → Change YOUR code to match EXISTING style
Do NOT change existing code to match your preferences
```

### Step 5: Orphan Cleanup

Check if YOUR changes created orphans:

```
Did your changes make something unused?
  - Unused imports that YOU made unused → Remove
  - Unused variables that YOU made unused → Remove
  - Unused functions that YOU made unused → Remove

Did you find pre-existing dead code?
  - Pre-existing unused imports → DON'T TOUCH. Mention in review.
  - Pre-existing dead functions → DON'T TOUCH. Mention in review.
```

## Common Violations

| Violation | Example | Fix |
|-----------|---------|-----|
| "Improved" naming | Renamed `getData()` → `fetchUserData()` | Revert. Not your task. |
| "Fixed" formatting | Re-indented adjacent code | Revert. Match existing. |
| "Added" error handling | Added try/catch to unrelated function | Revert. Not in spec. |
| "Cleaned up" imports | Sorted all imports alphabetically | Revert. Only touch yours. |
| "Updated" comments | Rewrote existing docstrings | Revert. Not your task. |
| "Refactored" nearby code | Extracted helper from adjacent function | Revert. Not broken, not yours. |
| Style preference | Changed `'` to `"` across file | Revert. Match existing. |

## The Trace Test

```
For EVERY changed line, complete this sentence:

"I changed this line because the task asked me to ___________."

Can't complete it? → Revert the line.
```

## Integration with Other Skills

**requesting-code-review:** Add "Diff Discipline" as a review dimension:
- Does every change trace to the spec?
- Any collateral file changes?
- Style consistency with existing code?

**subagent-driven-development:** After implementer subagent completes:
- Run diff audit before dispatching to reviewer
- Flag any suspicious scope expansion

**verification-before-completion:** Before claiming done:
- `git diff --stat` shows expected file count
- No unrelated changes slipped in

## Red Flags — STOP

If you catch yourself:
- "While I'm here, let me also..." → NO. Separate task or don't do it.
- "This variable name is misleading" → Not your task. Mention it, don't fix it.
- "The formatting is inconsistent" → Match the inconsistency. Don't fix it.
- "I should add error handling here" → Was it asked for? No? Skip it.
- "This could be more readable" → Readability refactors are separate tasks.
- "Let me update the comments too" → Only if YOUR changes make them wrong.

## The Bottom Line

```
The test: git diff should surprise no one.
Every change expected. Nothing extra. Nothing missing.
```
