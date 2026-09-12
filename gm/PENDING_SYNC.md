# PENDING SYNC — TIANDAO-WORLD

## Purpose
Temporary synchronization protocol for gameplay sessions where the AI Game Master can read/verify GitHub but cannot write back to the repository.

## Core Principle
`PENDING SYNC` is not Canon and is not automatically trusted state. It is a transfer package containing gameplay results that must be reviewed and validated by the Admin before becoming persistent repository state.

## Workflow
`Qwen Gameplay → Validated Turn → PENDING SYNC Package → Admin Review → Fresh GitHub Fetch → Validate → Apply Current State/History → Commit → Fetch Again → Verify → Clear/Archive Pending`

## GM Rules
When repository write-back is unavailable or fails:
- Do not claim the repository is synchronized.
- Continue from the last successfully validated operational state so the story does not regress to an older repository snapshot.
- Mark material changes as `PENDING SYNC`.
- Record Before → After, World Time, entity ID, cause, resolution, and Origin/source for every material change.
- Do not overwrite or reinterpret the older GitHub state as the current gameplay state.
- Do not invent missing values to complete the package.
- On the next sync, the Admin must fresh-fetch the repository before applying any pending change.

## Pending Sync Package
Use this compact format when handing gameplay results to the Admin:

```text
PENDING SYNC

Player ID: [PLAYER-ID]
Character ID: [CHARACTER-ID]
Beast ID(s): [BEAST-ID / NONE]

Last Repository State Verified:
[brief verified repository state/reference]

Last Operational State:
[latest validated gameplay state]

World Time:
[Year | Season | Date | Month | Day | Weather | Hour]

Changes:
- Entity ID:
- Field:
- Before:
- After:
- Cause:
- Resolution:
- Origin/Source:

Material Events / History:
- [confirmed event]

Active Threads / World Impact:
- [if applicable]

Pending Status:
PENDING SYNC
```

## Admin Sync Procedure
1. Receive the Pending Sync Package from the GM/player.
2. Identify the active Player ID, Character ID, and any BEAST_ID involved.
3. Fresh-fetch the current repository state, relevant History, World State, Active Threads, Timeline, and applicable rules.
4. Compare the package against the latest verified repository state and known history.
5. Validate every claimed transition. Player intent or GM claim alone is not proof of a material state change.
6. Reject, correct, or split any unsupported transition instead of forcing it into the repository.
7. Apply only validated changes to the correct Current State and History files.
8. Add required Origin Log entries and preserve entity isolation.
9. Commit the validated changes.
10. Fresh-fetch the written files and verify the resulting state.
11. Only after verification is the change considered synchronized.
12. Archive or mark the processed package as `SYNCED`; unresolved items remain `PENDING SYNC`.

## Entity Isolation
- Character changes belong to the active Character ID.
- Character History belongs only to that Character ID.
- Spirit Beast changes belong to the relevant BEAST_ID.
- Beast History belongs only to that BEAST_ID.
- Shared World State/Active Threads/Timeline are updated only when the event genuinely has shared scope.
- Never copy one entity's private state into another entity.

## Conflict Rules
Priority remains:
`Canon/Admin/Custom → System Resolution → Current Verified Repository State → Validated Pending Sync → Persistent Memory → Player Intent`.

If Pending Sync conflicts with newer verified repository data, do not blindly overwrite the repository. Reconcile the conflict using Origin Logs/History and keep only transitions that can be proven.

## Status
- `PENDING SYNC` = gameplay result not yet written/verified in repository.
- `SYNCED` = Admin applied, committed, re-fetched, and verified the result.
- `REJECTED` = claimed transition failed validation and must not enter persistent state.
- `PARTIAL` = some transitions were validated and synced while others remain pending/rejected.

## Hard Rules
- Pending Sync never becomes Canon merely because it came from the GM.
- Never erase a newer repository state with an older gameplay package.
- Never claim write-back success without verification.
- Never use a pending package to justify retroactive changes.
- Missing information remains `???`.
