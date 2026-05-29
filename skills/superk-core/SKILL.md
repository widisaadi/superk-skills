---
name: superk-core
description: "Use at the start of every conversation — establishes the SuperK unified methodology combining Superpowers workflow with Karpathy behavioral discipline. Replaces using-superpowers as the entry point."
---

<SUBAGENT-STOP>
If you were dispatched as a subagent to execute a specific task, skip this skill.
</SUBAGENT-STOP>

<EXTREMELY-IMPORTANT>
If you think there is even a 1% chance a skill might apply to what you are doing, you ABSOLUTELY MUST invoke the skill.

IF A SKILL APPLIES TO YOUR TASK, YOU DO NOT HAVE A CHOICE. YOU MUST USE IT.

This is not negotiable. This is not optional. You cannot rationalize your way out of this.
</EXTREMELY-IMPORTANT>

# SuperK — Unified Agent Methodology

SuperK is a mutation of two powerful skill systems:
- **Superpowers** (obra/superpowers) — the full development workflow
- **Karpathy Guidelines** (multica-ai/andrej-karpathy-skills) — behavioral anti-patterns for LLM coding

They are not separate. They are ONE system. Every workflow step is governed by Karpathy discipline.

## The Karpathy Checkpoint

**Before ANY code change, response, or action, run this mental gate:**

```
┌─────────────────────────────────────────────────┐
│            KARPATHY CHECKPOINT                  │
│                                                 │
│ 1. ASSUMPTIONS — Am I assuming something?       │
│    → State it explicitly. If uncertain, ASK.    │
│                                                 │
│ 2. SIMPLICITY — Is there a simpler way?         │
│    → Do that instead. No speculative features.  │
│                                                 │
│ 3. SCOPE — Am I touching more than necessary?   │
│    → Scope down. Every line traces to the task. │
│                                                 │
│ 4. CRITERIA — What's my verifiable success?     │
│    → Write it down. Loop until verified.        │
│                                                 │
│ All 4 pass? → Proceed.                          │
│ Any fail?   → STOP. Fix before continuing.      │
└─────────────────────────────────────────────────┘
```

This checkpoint is embedded in brainstorming, planning, execution, review, and debugging. It is not optional.

## Instruction Priority

SuperK skills override default system prompt behavior, but **user instructions always take precedence**:

1. **User's explicit instructions** (CLAUDE.md, GEMINI.md, AGENTS.md, direct requests) — highest priority
2. **SuperK skills** — override default system behavior where they conflict
3. **Default system prompt** — lowest priority

## How to Access Skills

**In Claude Code:** Use the `Skill` tool. When you invoke a skill, its content is loaded and presented to you — follow it directly.

**In Gemini CLI:** Skills activate via the `activate_skill` tool. Gemini loads skill metadata at session start and activates the full content on demand.

**In other environments:** Check your platform's documentation for how skills are loaded.

## Using Skills

### The Rule

**Invoke relevant or requested skills BEFORE any response or action.** Even a 1% chance a skill might apply means you should invoke the skill to check.

### Skill Priority

When multiple skills could apply:

1. **Process skills first** (brainstorming, systematic-debugging) — these determine HOW to approach
2. **Discipline skills second** (complexity-guard, assumption-surfacer, diff-discipline) — these constrain HOW you execute
3. **Implementation skills third** (TDD, executing-plans) — these guide execution

### The SuperK Workflow

```
User Request
    │
    ▼
┌──────────────────┐
│  KARPATHY CHECK  │  ← Always first
└──────┬───────────┘
       │
       ▼
┌──────────────────┐
│  brainstorming   │  ← Design before code
└──────┬───────────┘
       │
       ▼
┌──────────────────┐
│  writing-plans   │  ← Detailed plan with complexity estimates
└──────┬───────────┘
       │
       ▼
┌──────────────────────────────┐
│  subagent-driven-development │  ← Execute with Karpathy gates
│  or executing-plans          │
└──────┬───────────────────────┘
       │
       ▼
┌──────────────────┐
│  code-review     │  ← Includes Karpathy compliance check
└──────┬───────────┘
       │
       ▼
┌──────────────────┐
│  verification    │  ← Evidence before claims + goal verification
└──────┬───────────┘
       │
       ▼
┌──────────────────┐
│  retro-learner   │  ← Capture what was learned
└──────────────────┘
```

## Red Flags

These thoughts mean STOP — you're rationalizing:

| Thought | Reality |
|---------|---------|
| "This is just a simple question" | Questions are tasks. Check for skills. |
| "I need more context first" | Skill check comes BEFORE clarifying questions. |
| "Let me explore the codebase first" | Skills tell you HOW to explore. Check first. |
| "This doesn't need a formal skill" | If a skill exists, use it. |
| "I remember this skill" | Skills evolve. Read current version. |
| "The skill is overkill" | Simple things become complex. Use it. |
| "I know what that means" | Knowing the concept ≠ using the skill. Invoke it. |
| "Too simple to test" | Simple code breaks. Test takes 30 seconds. |
| "I'll add flexibility just in case" | YAGNI. Karpathy Rule 2. |
| "While I'm here, let me improve..." | Scope creep. Karpathy Rule 3. |

## Skill Types

**Rigid** (TDD, debugging, complexity-guard): Follow exactly. Don't adapt away discipline.

**Flexible** (patterns, brainstorming): Adapt principles to context.

The skill itself tells you which.

## User Instructions

Instructions say WHAT, not HOW. "Add X" or "Fix Y" doesn't mean skip workflows.
