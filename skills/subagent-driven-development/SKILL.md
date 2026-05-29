---
name: subagent-driven-development
description: "Executes implementation plans via subagents. Fresh subagent per task + 2-stage review."
---

# Subagent-Driven Development

Execute plans by dispatching a fresh subagent for EACH task. Keep your context clean. Do not pause between tasks unless blocked.

## Core Principle
Fresh subagent per task + Karpathy Checkpoint + Two-stage review (Spec → Quality) = Fast, high-quality iteration.

## The Process (Per Task)
1. **Read task** from plan.
2. **Dispatch Implementer** subagent. Give it the exact task text + Karpathy Checkpoint.
3. **Implementer works** (TDD, commit).
4. **Dispatch Spec Reviewer** subagent. Does code match the plan EXACTLY? No extra features?
   - *If no:* Implementer fixes. Re-review.
5. **Dispatch Code Quality Reviewer**. Does it meet standards?
   - *If no:* Implementer fixes. Re-review.
6. **Mark task complete** in plan.
7. Move to next task immediately.

## SuperK Karpathy Integration
Inject this checkpoint into EVERY implementer subagent's prompt:
```text
Before writing ANY code:
1. ASSUMPTIONS — State what you're assuming. If uncertain, ask.
2. SIMPLICITY — Write minimum code. No speculative features.
3. SCOPE — Touch only files in the task spec. Nothing extra.
4. CRITERIA — Define verifiable success. Loop until verified.
```

## Subagent Status Handling
- **DONE**: Proceed to Spec Review.
- **DONE_WITH_CONCERNS**: Read concerns. If about correctness, fix before review. If observation, proceed.
- **NEEDS_CONTEXT**: Provide context, re-dispatch.
- **BLOCKED**: Assess blocker. Provide context, use smarter model, or escalate to user.

## Red Flags (Never Do These)
- ❌ Skip reviews (spec or quality).
- ❌ Do quality review before spec review passes.
- ❌ Let implementer add features NOT in the spec (Scope Creep).
- ❌ Accept >2x estimated lines without justification (Complexity Guard).
- ❌ Make subagent read the plan file (feed them the specific text).
- ❌ Parallelize implementers on dependent tasks.
