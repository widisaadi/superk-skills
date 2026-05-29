---
name: test-driven-development
description: "Use when implementing ANY feature or bugfix. NO PRODUCTION CODE WITHOUT A FAILING TEST FIRST."
---

# Test-Driven Development (TDD)

## The Iron Law
**NO PRODUCTION CODE WITHOUT A FAILING TEST FIRST.**
If you wrote code before the test, delete it. Start over. No exceptions.

## Red-Green-Refactor Cycle

### 1. RED (Write Failing Test)
- Write ONE minimal test for the desired behavior.
- **Verify RED:** Run the test. MUST fail for the expected reason (not a syntax error).
- *If it passes immediately, your test is wrong. Fix it.*

### 2. GREEN (Minimal Code)
- Write the absolute simplest code to pass the test.
- Do NOT add extra features, do NOT handle edge cases you didn't write tests for. YAGNI.
- **Verify GREEN:** Run the test. MUST pass.

### 3. REFACTOR (Clean Up)
- Clean up duplication, improve names.
- Keep tests green. Do NOT add new behavior here.

## Rationalizations (STOP if you think these)
- ❌ "This is too simple to test." (Simple code breaks).
- ❌ "I'll test it after." (Tests-after prove nothing).
- ❌ "Deleting code is wasteful." (Sunk cost fallacy. Delete it).
- ❌ "I manually tested it." (Ad-hoc ≠ systematic).

## Bug Fixes
Found a bug? 
1. Write a test that reproduces the bug (RED).
2. Fix the code (GREEN).

**Final Rule:** If you didn't watch the test fail, you don't know if it tests the right thing.
