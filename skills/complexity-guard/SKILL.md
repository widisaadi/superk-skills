---
name: complexity-guard
description: "Use before and during any code implementation to prevent overengineering, unnecessary abstractions, and scope creep. Enforces Karpathy Rule 2 (Simplicity First) with concrete checks."
---

# Complexity Guard

## Overview

LLM agents consistently over-build. They add abstractions "for flexibility," create helper classes for single-use code, and import libraries for tasks that take 10 lines. This skill is the antidote.

**Core principle:** The best code is the code you didn't write. Every line must justify its existence.

**This is a RIGID skill.** Follow exactly. Don't adapt away discipline.

## When to Use

- Before writing any implementation code
- During code review (self or peer)
- When plan estimates are exceeded
- When tempted to add "just one more" feature

## The Three Gates

### Gate 1: Line Budget

Every task in the plan should have an estimated line count. Before implementing:

```
ESTIMATED: ~50 lines
ACTUAL so far: 47 lines → ✅ Proceed
ACTUAL so far: 120 lines → ❌ STOP

If ACTUAL > 2x ESTIMATED:
  1. STOP writing code
  2. List what you built vs. what was asked
  3. Identify what's extra
  4. Delete the extras
  5. If estimate was wrong (not scope creep), note it for retro
```

**No exceptions.** If you're building more than expected, something is wrong.

### Gate 2: Abstraction Tax

Every new abstraction must pass this test:

| Abstraction | Question | Pass if... |
|-------------|----------|------------|
| New class/interface | How many callers? | ≥ 2 callers exist TODAY (not "might need later") |
| New helper function | Could this be inline? | Inline version is >5 lines AND used >1 time |
| New file | Does existing file make sense? | Existing file would exceed ~200 lines |
| New config option | Who asked for this? | User explicitly requested it |
| New error type | Is this a distinct recovery path? | Different handling required |
| Generic type parameter | Do concrete types vary TODAY? | ≥ 2 concrete types exist now |

**If abstraction fails the test → delete it. Inline the code.**

Common violations:
- `interface IRepository` with one implementation → delete interface
- `class UserService` wrapping 3 lines → inline the 3 lines
- `utils/helpers.ts` for one function → put function where it's used
- `config.maxRetries` when it's always 3 → hardcode 3

### Gate 3: Dependency Audit

Before adding ANY external dependency:

```
1. What does it do?
2. Can I do this in <20 lines without it?
   - YES → Write the 20 lines. Skip the dependency.
   - NO → Proceed to step 3.
3. Is this a well-maintained package? (>1000 stars, recent commits)
   - NO → Write it yourself or find alternative.
   - YES → Add it.
4. Am I using >10% of this package's features?
   - NO → Consider writing just what you need.
   - YES → Add it.
```

**Common offenders:**
- `lodash` for `_.get()` → use optional chaining
- `moment` for date formatting → use `Intl.DateTimeFormat`
- `axios` for one HTTP call → use `fetch`
- `uuid` for one ID → use `crypto.randomUUID()`

## Integration with Other Skills

**writing-plans:** Add `~estimated lines` to each task:
```markdown
### Task 3: Add validation (~30 lines)
```

**requesting-code-review:** Reviewer checks complexity gates:
- Any abstraction with only 1 caller?
- Any dependency used for <10% of features?
- Any file >200 lines that could be split?

**verification-before-completion:** Before claiming done:
- Actual lines vs estimated — any >2x overrun?
- Any "while I'm here" additions?

## Red Flags — STOP

If you catch yourself thinking:
- "This might be useful later" → YAGNI. Delete it.
- "Let me add a config option for this" → Hardcode it.
- "I'll create a base class for extensibility" → You have 1 class. No base needed.
- "This utility could be reused" → Is it reused TODAY? No? Inline it.
- "Let me add proper error handling" → For what scenario? If impossible, skip it.
- "I should wrap this in an abstraction" → Why? 1 caller = no abstraction.
- "Just one more helper" → That's how 50-line tasks become 200-line tasks.

## The Bottom Line

```
Would a senior engineer say "this is overcomplicated"?
YES → Simplify until they wouldn't.
```

Simple code is not lazy code. Simple code is disciplined code.
