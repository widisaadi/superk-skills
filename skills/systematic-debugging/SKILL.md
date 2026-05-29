---
name: systematic-debugging
description: "Use for ANY bug, test failure, or unexpected behavior. NO FIXES WITHOUT ROOT CAUSE INVESTIGATION."
---

# Systematic Debugging

**The Iron Law: NO FIXES WITHOUT ROOT CAUSE INVESTIGATION FIRST.**
Guess-and-check wastes time and creates new bugs.

## The Four Phases (Must be sequential)

### 1. Root Cause Investigation
- Read errors carefully. Don't skim.
- Reproduce the issue consistently.
- Trace data flow backward from the error to the source.
- *If multi-component:* Add logging at boundaries to see exactly where data drops/corrupts before fixing.

### 2. Pattern Analysis
- Find working examples of similar code in the project.
- Compare broken vs. working. What is exactly different?

### 3. Hypothesis & Testing
- Form a single hypothesis: "I think X is the cause because Y."
- Test it minimally (don't fix 3 things at once).
- Verify if the hypothesis was right before moving on.

### 4. Implementation
- **Write a failing test** reproducing the issue (TDD).
- Implement the single fix at the root cause (not the symptom).
- **Verify Fix:** Test passes, no regressions.
- *Failed 3+ times?* STOP. You have an architectural problem, not a simple bug. Discuss with the user.

## Red Flags (STOP and go back to Phase 1)
- ❌ "I'll just try changing X and see if it works."
- ❌ "I'll add a quick fix for now, investigate later."
- ❌ "Let me add multiple changes at once."
- ❌ "I don't fully understand it, but this might work."

If you are guessing, you are not debugging.
