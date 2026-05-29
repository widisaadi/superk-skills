---
name: requesting-code-review
description: "Use to dispatch a code reviewer subagent. Mandatory after tasks, major features, or before merge."
---

# Requesting Code Review

Dispatch a code reviewer subagent to catch issues before they cascade. 

## How to Request
1. **Get git SHAs:**
   `BASE_SHA=$(git rev-parse HEAD~1)`
   `HEAD_SHA=$(git rev-parse HEAD)`
2. **Dispatch Reviewer:** Use template `code-reviewer.md` (Provide DESCRIPTION, PLAN_OR_REQUIREMENTS, BASE_SHA, HEAD_SHA).
3. **Act on Feedback:** Fix Critical & Important issues BEFORE proceeding. Note Minor ones.

## Karpathy Compliance Review (SuperK)
Every review MUST check:
- **Simplicity:** Any unnecessary abstractions/generics?
- **Surgical Scope:** Did files change that weren't in the spec?
- **Assumption Clarity:** Are assumptions documented?
- **Goal Verification:** Are success criteria actually tested?
- **Line Budget:** >2x line overrun?
*Flag violations as Important.*

## Red Flags
- ❌ Skip review because "it's simple"
- ❌ Proceed with unfixed Important issues
- ❌ Skip Karpathy compliance check
- ❌ Accept scope creep without discussion
