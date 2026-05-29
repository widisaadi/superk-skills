# SuperK (Superpowers + Andrej Karpathy Skills)

**SuperK** is a unified AI agent methodology born from combining two exceptional skill systems — then mutating them into something greater than the sum of their parts.

- **[Superpowers](https://github.com/obra/superpowers)** — A complete software development workflow (brainstorming → planning → TDD → execution → debugging → verification → code review)
- **[Andrej Karpathy Skills](https://github.com/multica-ai/andrej-karpathy-skills)** — Behavioral guidelines to reduce common LLM coding mistakes (assumptions, simplicity, surgical changes, goal-driven execution)

I really love these skills, which is why I didn't just bundle them — I **fused** them. Karpathy's discipline is injected into every step of the Superpowers workflow, plus 5 new "mutant" skills fill the gaps neither project addresses alone.

---

## 🧬 What Makes SuperK a "Mutant"

| Gap in Superpowers | Gap in Karpathy | SuperK Solution |
|---|---|---|
| No anti-bloat enforcement | Rules but no enforcement mechanism | `complexity-guard` skill |
| No assumption tracking | "Surface assumptions" but no structure | `assumption-surfacer` skill |
| No surgical change enforcement | "Touch only what you must" but no check | `diff-discipline` skill |
| No learning loop | No learning loop | `retro-learner` skill |
| Karpathy rules not referenced | Not integrated into any workflow | Karpathy DNA injected into all workflow skills |
| Entry point is generic | Standalone skill | `superk-core` unified entry point |

---

## 🧩 Skills Overview

### Core
- **superk-core** — Unified entry point with the Karpathy Checkpoint embedded
- **karpathy-guidelines** — The 4 behavioral rules (Think, Simplify, Scope, Verify)

### Workflow (from Superpowers, enhanced with Karpathy DNA)
- **brainstorming** — Design before code, now with assumption surfacing + simplicity gate
- **writing-plans** — Detailed plans, now with complexity estimates + assumptions per task
- **executing-plans** — Batch execution with checkpoints
- **subagent-driven-development** — Fresh subagent per task, now with Karpathy checkpoint in every dispatch
- **using-git-worktrees** — Parallel development branches
- **finishing-a-development-branch** — Merge/PR decision workflow
- **dispatching-parallel-agents** — Concurrent subagent workflows

### Quality (from Superpowers, enhanced)
- **test-driven-development** — RED-GREEN-REFACTOR cycle
- **systematic-debugging** — 4-phase root cause process
- **requesting-code-review** — Now includes Karpathy compliance review dimension
- **receiving-code-review** — Responding to feedback
- **verification-before-completion** — Now includes goal verification + diff scope check

### Mutant Skills (NEW — SuperK originals)
- **complexity-guard** — Line Budget, Abstraction Tax, Dependency Audit
- **assumption-surfacer** — CERTAIN/LIKELY/UNCERTAIN classification system
- **diff-discipline** — Post-implementation diff audit before every commit
- **retro-learner** — Capture learnings, track Karpathy violations, improve over time

### Meta
- **writing-skills** — Create new skills following best practices
- **using-superpowers** — Original Superpowers entry point (kept for compatibility)

---

## 🚀 Installation

Install SuperK into your project:

```bash
npx degit widisaadi/superk-skills ./skills
```

---

## 💡 How to Use

**Option 1: Explicit Mention**
Just mention **superk** in your prompt. The agent will automatically utilize the combined methodology.
> "Agent, use **superk** to build this feature."

**Option 2: Auto-Run (Recommended)**
By default, this repository includes a `CLAUDE.md` and `AGENT.md` file at the root. If you are using Claude Code, Cursor, or Gemini Antigravity, the agent will **automatically read these files** and invoke `superk-core` on every task without you needing to mention it.

The Karpathy Checkpoint runs before every action:

```
┌─────────────────────────────────────────────────┐
│            KARPATHY CHECKPOINT                  │
│                                                 │
│ 1. ASSUMPTIONS — Am I assuming something?       │
│ 2. SIMPLICITY  — Is there a simpler way?        │
│ 3. SCOPE       — Am I touching more than needed?│
│ 4. CRITERIA    — What's my verifiable success?  │
└─────────────────────────────────────────────────┘
```

---

## 📄 License

This project uses the **MIT License**.

It combines and extends open-source work from:
- [Superpowers](https://github.com/obra/superpowers) (MIT License)
- [Andrej Karpathy Skills](https://github.com/multica-ai/andrej-karpathy-skills) (MIT License)