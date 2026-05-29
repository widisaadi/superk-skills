---
name: brainstorming
description: "Use before ANY creative work (features, components, etc.). Explores intent, requirements, and design."
---

# Brainstorming

<HARD-GATE>NO implementation until design is presented and approved by user. Even for "simple" tasks.</HARD-GATE>

## Checklist (Complete in order)
1. **Explore context** — Check files/docs.
2. **Check learnings** — Read `docs/superk/learnings.md` for past traps.
3. **Offer visual companion** — Separate message if visual questions are coming (see below).
4. **Clarifying questions** — Ask ONE at a time.
5. **Surface assumptions** — List & classify (CERTAIN/LIKELY/UNCERTAIN). Resolve UNCERTAIN.
6. **Propose 2-3 approaches** — Option 1 MUST be the minimal viable approach (Karpathy Rule 2).
7. **Present design** — Get user approval per section.
8. **Write spec doc** — Save to `docs/superpowers/specs/YYYY-MM-DD-<topic>-design.md`.
9. **Spec self-review** — Fix placeholders/ambiguity inline.
10. **User review** — Wait for user approval on spec file.
11. **Transition** — Invoke `writing-plans` skill.

## Key Rules
- **One question per message.** Focus on purpose, constraints, success criteria.
- **YAGNI.** Simplest approach wins unless complexity is justified.
- **Isolate & Bound.** Break systems into clear, independent units.
- **Follow existing patterns.** Do not propose unrelated refactoring.

## Visual Companion
If visual questions (mockups, diagrams) are expected, offer the companion in a standalone message:
> "Some of what we're working on might be easier to explain if I can show it to you in a web browser. I can put together mockups, diagrams, comparisons, and other visuals as we go. This feature is still new and can be token-intensive. Want to try it? (Requires opening a local URL)"

- If accepted, read `skills/brainstorming/visual-companion.md`.
- Use browser ONLY for visuals. Use terminal for concepts/text choices.
