---
name: assumption-surfacer
description: "Use before any implementation to explicitly identify, classify, and resolve assumptions. Enforces Karpathy Rule 1 (Think Before Coding) with structured assumption tracking."
---

# Assumption Surfacer

## Overview

LLM agents silently pick interpretations and build on unverified assumptions. This skill forces every assumption into the open before a single line of code is written.

**Core principle:** Hidden assumptions are hidden bugs. Surface them all, resolve the uncertain ones.

**This is a RIGID skill.** Follow exactly. Don't adapt away discipline.

## When to Use

- Before implementing any task from a plan
- During brainstorming when exploring approaches
- When modifying existing code you don't fully understand
- When a task description has any ambiguity

## The Assumption Register

Before starting implementation, create an assumption register:

```markdown
## Assumptions for Task N: [Task Name]

| # | Assumption | Confidence | Resolution |
|---|-----------|------------|------------|
| 1 | API returns JSON with `data` wrapper | CERTAIN | Verified in existing code at `src/api.ts:45` |
| 2 | Users table has `email` column | CERTAIN | Checked schema migration |
| 3 | Rate limit is 100 req/min | LIKELY | Based on docs, not tested |
| 4 | WebSocket reconnects automatically | UNCERTAIN | Need to verify library behavior |
| 5 | Auth token expires after 1 hour | UNCERTAIN | Docs unclear, need to test |
```

### Confidence Levels

**CERTAIN** — Verified in code, docs, or tests. Proceed.
- "I read the function signature at `file.ts:123`"
- "The test at `test.ts:45` confirms this behavior"
- "The migration at `001_create_users.sql` shows this schema"

**LIKELY** — Reasonable inference, but not directly verified. Note in code.
- "Docs suggest this, but I haven't tested"
- "Similar pattern used elsewhere in codebase"
- "Standard behavior for this library"
- → Add a code comment: `// Assumption: [what you assumed] — verify if issues arise`

**UNCERTAIN** — Could go either way. MUST resolve before coding.
- "Docs don't mention this"
- "Multiple interpretations possible"
- "Depends on runtime environment"
- → STOP. Ask the user, check the code, or write a quick test.

## The Process

### Step 1: List All Assumptions

Read the task spec. For every decision point, ask:
- What am I assuming about the **input** (data format, types, ranges)?
- What am I assuming about the **environment** (OS, runtime, dependencies)?
- What am I assuming about the **existing code** (behavior, contracts, side effects)?
- What am I assuming about the **requirements** (what "correct" means, edge cases)?

### Step 2: Classify Each

Assign CERTAIN, LIKELY, or UNCERTAIN to each assumption.

### Step 3: Resolve UNCERTAIN

For each UNCERTAIN assumption:
1. Can I verify in the codebase? → Read the code. Upgrade to CERTAIN.
2. Can I verify with a quick test? → Write a one-off test. Upgrade to CERTAIN.
3. Multiple interpretations? → Present them to the user. Ask which one.
4. Can't determine? → Ask the user explicitly.

**Do NOT proceed with UNCERTAIN assumptions.** That's building on quicksand.

### Step 4: Document LIKELY

For each LIKELY assumption, add a code comment at the relevant location:
```typescript
// Assumption: Redis connection pool defaults to 10 connections
// Source: Library docs, not explicitly tested
// If this causes issues, check actual pool size with redis.options
const pool = createRedisPool();
```

### Step 5: Proceed

Once all assumptions are CERTAIN or LIKELY (with comments), begin implementation.

## Integration with Other Skills

**brainstorming:** During design, surface assumptions about:
- User needs and constraints
- Technical feasibility
- Performance requirements
- Integration points

**writing-plans:** Each task includes an assumptions section:
```markdown
### Task 3: Add email validation (~30 lines)

**Assumptions:**
- Email format follows RFC 5322 (CERTAIN — standard)
- Duplicate emails should be rejected (CERTAIN — spec section 2.1)
- Email check is case-insensitive (LIKELY — standard practice)
```

**systematic-debugging:** When debugging, check assumption register first:
- Did a LIKELY assumption turn out wrong?
- Was there an assumption you missed entirely?

## Red Flags — STOP

If you catch yourself:
- "This is obviously how it works" → Is it? Verify.
- "Everyone knows that..." → Document it anyway.
- "The API probably returns..." → PROBABLY is UNCERTAIN. Check.
- Picking one interpretation without mentioning alternatives → Surface all options.
- "I'll figure this out as I go" → No. Assumptions before code.
- Modifying code without reading the surrounding context → You're assuming behavior.

## The Bottom Line

```
Every silent assumption is a bug waiting to happen.
Make them loud. Make them visible. Make them verified.
```
