---
name: retro-learner
description: "Use after completing a feature branch or significant piece of work to capture learnings, track Karpathy violations, and improve future work. Auto-triggers after finishing-a-development-branch."
---

# Retro Learner

## Overview

Without a learning loop, you repeat the same mistakes. This skill captures what went well, what went wrong, and what patterns to watch for — then feeds those learnings into future brainstorming and planning sessions.

**Core principle:** Every completed feature is a lesson. Capture it or lose it.

**This is a FLEXIBLE skill.** Scale the retro to the work — 2 minutes for a small fix, 10 minutes for a major feature.

## When to Use

- After `finishing-a-development-branch` completes
- After a debugging session that took >30 minutes
- After any task where the plan had to be significantly revised
- When the user asks for a retrospective

## The Quick Retro (< 5 minutes)

For small features and fixes:

```markdown
## Retro: [Feature/Fix Name] — [Date]

### What went well
- [1-2 bullet points]

### What surprised us
- [Unexpected behavior, wrong assumptions, or scope changes]

### Karpathy Violations
- [ ] Over-built (added features not requested)
- [ ] Under-specified (assumptions not surfaced)
- [ ] Scope creep (touched files outside spec)
- [ ] Weak success criteria (had to re-verify)

### Lesson
[One sentence: what to remember for next time]
```

## The Full Retro (5-10 minutes)

For major features:

```markdown
## Retro: [Feature Name] — [Date]

### Summary
[What was built, in 1-2 sentences]

### Metrics
- **Planned tasks:** [N]
- **Actual tasks:** [N] (include added/removed tasks)
- **Estimated lines:** [N]
- **Actual lines:** [N]
- **Plan revisions:** [N] times the plan was changed during execution
- **Debug sessions:** [N] times systematic-debugging was invoked
- **Review rounds:** [N] total review cycles across all tasks

### What went well
- [Specific things that worked]
- [Patterns that should be repeated]

### What went wrong
- [Specific problems encountered]
- [Where the plan was wrong]
- [Where assumptions failed]

### Karpathy Violations
For each violation, note what triggered it and how it was caught:

| Rule | Violation | How Caught | Prevention |
|------|-----------|-----------|------------|
| Rule 1 (Assumptions) | Assumed API returns array, actually returns object | Test failure | Should have checked API docs first |
| Rule 2 (Simplicity) | Built config system for 1 option | Code review | Use complexity-guard line budget |
| Rule 3 (Surgical) | Reformatted adjacent code | diff-discipline | Run diff audit before commit |
| Rule 4 (Goals) | "Make it work" criteria | Had to re-verify 3 times | Define specific assertions upfront |

### Lessons Learned
1. [Actionable lesson for future work]
2. [Pattern to watch for]
3. [Tool/technique that helped or would have helped]

### Impact on Future Work
- [Changes to make in brainstorming process]
- [New assumptions to always check]
- [Complexity patterns to watch for]
```

## Where to Save

Save retros to: `docs/superk/retros/YYYY-MM-DD-[topic].md`

Maintain an index at: `docs/superk/learnings.md`

```markdown
# SuperK Learnings Index

## Key Patterns
- [Pattern]: [What to do about it] (from [retro link])
- [Pattern]: [What to do about it] (from [retro link])

## Common Assumptions to Verify
- [Assumption type]: [How to verify] (learned from [retro link])

## Complexity Traps
- [Trap]: [How to avoid] (from [retro link])

## Retro Log
| Date | Topic | Key Lesson |
|------|-------|------------|
| 2026-01-15 | Auth system | Always check token expiry assumptions |
| 2026-01-20 | API refactor | Line budget caught 3x overrun early |
```

## Integration with Other Skills

**brainstorming:** At the start of brainstorming, check `docs/superk/learnings.md`:
- Any relevant past lessons for this type of work?
- Any common assumptions to verify upfront?
- Any complexity traps to watch for?

**writing-plans:** Reference learnings when estimating complexity:
- "Last time a similar task was estimated at 30 lines but took 90"
- "Past retro noted this API has surprising behavior"

**finishing-a-development-branch:** After branch is finished:
- Trigger retro-learner automatically
- Ask: "Quick retro or full retro?"

## The Retro Checklist

After every completed piece of work:

- [ ] Run retro (quick or full, scaled to the work)
- [ ] Log any Karpathy violations
- [ ] Extract lessons for `learnings.md`
- [ ] Commit retro document
- [ ] Note any changes to future process

## Red Flags

- Skipping retro because "it went fine" → "Fine" means quick retro, not no retro
- Retro is all positive → What assumptions did you make? Were they all right?
- No Karpathy violations noted → Really? Check the diff for scope creep.
- Lessons are vague ("be more careful") → Make them specific and actionable

## The Bottom Line

```
The best agent is the one that makes new mistakes, not the same ones.
Capture. Learn. Improve.
```
