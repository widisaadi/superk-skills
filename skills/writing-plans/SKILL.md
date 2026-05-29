---
name: writing-plans
description: "Use when you have an approved design. Writes detailed, bite-sized implementation plans before coding."
---

# Writing Plans

Write plans as if the executing agent has ZERO context. Provide exact code, file paths, and test commands for every step. DRY. YAGNI. TDD. 

**Save to:** `docs/superpowers/plans/YYYY-MM-DD-<feature-name>.md`

## Plan Document Header
```markdown
# [Feature Name] Implementation Plan
> **Required Skill:** Use `subagent-driven-development` to implement this plan task-by-task.
**Goal:** [One sentence]
**Architecture:** [2-3 sentences]
**Tech Stack:** [Tools/Libraries]
---
```

## Task Structure (Every task MUST look like this)
````markdown
### Task N: [Component Name] (~estimated lines)

**Files:**
- Create: `path/to/file.py`
- Modify: `path/to/existing.py:123-145`

**Assumptions:** (SuperK Integration)
- [Assumption 1] — CERTAIN (verified at file:line)
- [Assumption 2] — LIKELY (will note in code)

- [ ] **Step 1: Write failing test**
```python
# Exact test code here
```
- [ ] **Step 2: Run test (must fail)**
Run: `npm test path/test.ts` (Expected: FAIL)
- [ ] **Step 3: Minimal implementation**
```python
# Exact implementation code here
```
- [ ] **Step 4: Run test (must pass)**
- [ ] **Step 5: Commit**
Run: `git commit -m "feat:..."`
````

## No Placeholders (Red Flags)
- ❌ "TBD", "TODO", "implement later"
- ❌ "Add error handling" (without providing the actual code)
- ❌ "Write tests for the above" (must provide test code)
- ❌ "Similar to Task N" (write it out fully)

## Self-Review before Handoff
1. **Spec coverage:** Does the plan cover every requirement?
2. **Placeholder scan:** Search and destroy "TBD"s.
3. **Type consistency:** Ensure function names match across tasks.

## Execution Handoff
When the plan is saved, ask the user:
> "Plan complete and saved. Shall we execute this using `subagent-driven-development`?"
