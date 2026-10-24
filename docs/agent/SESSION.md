# Threadly CRM — Session / Checkpoint

_Last updated: 2026-10-24_

## Current Objective

Implement the agent **context-management workflow** for this repository. Setup task, **not** an application task. **Complete.**

## Acceptance Criteria

- One canonical home for the workflow, no duplication, nothing lost.
- `PROJECT_CONTEXT.md` + `SESSION.md` reflect the **real** repo state (design stage).
- No application code modified.

## Current Status

- **Context workflow fully set up and consolidated.**
- Repo remains at the **design/requirements** stage; **no application code exists yet**.

## Files (final state)

- **`CLAUDE.md`** — canonical, slimmed: context-management workflow + pointers to
  `REQUIREMENTS.md` and `docs/agent/*`. (User: prefers `CLAUDE.md`; use these files
  as standing reference always.)
- **`docs/agent/PROJECT_CONTEXT.md`** — architecture, confirmed decisions,
  conventions, planned modules marked *not built*, open questions.
- **`docs/agent/SESSION.md`** — this checkpoint.
- **`AGENT.md` — DELETED** (redundant; its workflow text is in `CLAUDE.md`, its
  project quick-reference in `PROJECT_CONTEXT.md`). Do **not** recreate it.
- `REQUIREMENTS.md` unchanged.

## Decisions & Constraints

- `CLAUDE.md` = single source of truth for agent rules; `docs/agent/` = deep/live state.
- Arrangement also saved to persistent memory (`agent-context-workflow`), so it
  survives a cleared context.
- No app to test; verify state from the file listing. Mark confirmed vs planned.

## Tests / Verification

- Confirmed repo listing: `CLAUDE.md`, `REQUIREMENTS.md`, `docs/agent/*` only.
  No `package.json`, no `payload.config.*`, no source tree, no `.git`.
- `AGENT.md` deletion verified (rm succeeded).

## Errors / Failed Approaches

- None.

## Remaining / Unresolved

- No `.git` repository — nothing to commit yet (init before first commit if desired).
- Open product questions per `REQUIREMENTS.md` / `PROJECT_CONTEXT.md`:
  payment gateway TBD, hosting open, admin/editor identities TBC.

## Exact Next Step

Begin application work: **scaffold the Payload CMS project** (first build step),
then start the **Catalog** module per `PROJECT_CONTEXT.md`. Re-run the repo
listing first to confirm state before scaffolding.
