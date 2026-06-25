# CLAUDE.md

Behavioral guidelines to reduce common LLM coding mistakes. Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

---

**These guidelines are working if:** fewer unnecessary changes in diffs, fewer rewrites due to overcomplication, and clarifying questions come before implementation rather than after mistakes.

<!-- BEGIN managed:host-paths v2 — do not edit between markers; identical across Gokhan's repos -->
## Host-specific paths (multi-machine)

This repo is worked on from three of Gokhan's machines. The repo lives at a
different absolute path on each. **Detect the host at runtime and resolve roots
from the matching row — never hard-code one machine's drive letters.** In
PowerShell use `$env:COMPUTERNAME`; in bash / git-bash use `hostname`.

| Machine  | Hostname          | GitHub root              | Google Drive    |
| -------- | ----------------- | ------------------------ | --------------- |
| Notebook | `GV20260527`      | `C:\Users\gokha\GitHub`  | `G:\My Drive`   |
| Desktop  | `GVAROL202411`    | `E:\GitHub`              | `J:\My Drive`   |
| Desktop2 | `DESKTOP-HF2AV4G` | `C:\Users\verek\Github`  | — (none)        |

`C:\Temp`, `C:\Tim`, and `C:\Data` are the same path on all machines.

If `$env:COMPUTERNAME` matches none of these hostnames, stop and ask rather than guessing.
<!-- END managed:host-paths v2 -->
