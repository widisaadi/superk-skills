---
name: verification-before-completion
description: "Use before claiming ANY task is done, fixed, or passing. EVIDENCE BEFORE CLAIMS, ALWAYS."
---

# Verification Before Completion

**The Iron Law: NO COMPLETION CLAIMS WITHOUT FRESH VERIFICATION EVIDENCE.**
Claiming work is complete without verification is dishonesty, not efficiency.

## The Gate Function (Run this before saying "It's done")
1. **IDENTIFY:** What command proves this claim?
2. **RUN:** Execute the FULL command.
3. **READ:** Read the full output.
4. **VERIFY:** Does the output confirm the claim?
5. **ONLY THEN:** Make the claim.

## Verification Requirements
| Claim | Required Evidence | Not Sufficient |
|-------|----------|----------------|
| Tests pass | Test output: 0 failures | "Should pass now" |
| Bug fixed | Test of original symptom passes | Code looks right |
| **Goals achieved** | **Karpathy success criteria verified** | "It works" |
| **Scope respected** | **`git diff --stat` (diff-discipline) passes** | "Only changed what was needed" |

## Red Flags (Never say these without evidence)
- ❌ "Should work now" (Run it!)
- ❌ "I'm confident" (Confidence ≠ evidence)
- ❌ "Linter passed" (Linter ≠ compiler/tests)
- ❌ "Agent said success" (Verify independently)

**Bottom Line:** Run the command. Read the output. THEN claim the result. No exceptions.
