# Threadly CRM — Agent Instructions

Single source of truth for agent context. Before substantial work, read:

- `REQUIREMENTS.md` — product scope & decision log
- `docs/agent/PROJECT_CONTEXT.md` — architecture, confirmed decisions, conventions
- `docs/agent/SESSION.md` — current task, recent changes, exact next step

## Context-management workflow (required)

Goal: keep active context small while preserving task progress, decisions, and unfinished work — continuity with minimal context usage, not just a shorter summary.

**Files:** `CLAUDE.md` (this — rules) · `docs/agent/PROJECT_CONTEXT.md` (architecture) · `docs/agent/SESSION.md` (live state). Create missing files; never overwrite useful info without reviewing it first.

**Monitor:** Watch context-window usage when available. ~70% → prepare a compact checkpoint; 80% → save a checkpoint before continuing substantial work. If usage isn't exposed, judge by task complexity, conversation length, and accumulated tool output. Never wait until near-exhaustion to preserve important information.

**Checkpoint:** Update `SESSION.md` at meaningful milestones, before long investigations, after significant changes, and before context exhaustion. Keep it concise — consolidate and drop obsolete lines, don't append. Structure: objective · acceptance criteria · status · files changed · decisions/constraints · verification · errors/failed approaches · remaining tasks · **exact next step** · key paths/commands. Facts only; separate verified results from assumptions.

**Compact:** Drop repeated explanations, stale debug output, finished-task detail, verbose logs/code that's re-fetchable, and superseded plans. Keep: objective & acceptance criteria, architecture/dependencies/conventions, confirmed decisions + why, key files/functions/config, implemented changes & status, errors + failed fixes, tests run + results, open issues/blockers, the exact next action, and must-not-violate constraints. Concise structured facts, not the verbatim transcript.

**Resume:** In a fresh window, read `CLAUDE.md`, `PROJECT_CONTEXT.md`, `SESSION.md` before proceeding. Verify actual repo state before assuming prior changes still exist. Resume from the recorded next step; re-run only the checks needed to establish current state. Don't repeat completed work.

**Save context:** Inspect only files relevant to the task; prefer targeted searches and small excerpts over full dumps; summarize command output; don't reread unchanged files; don't paste large code blocks when a path + brief description suffices; never claim tests passed unless actually run; don't discard unresolved problems or must-have constraints.
