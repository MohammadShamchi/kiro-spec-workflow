---
description: Execute the next unchecked spec subtask (one at a time, resumable)
argument-hint: [optional: <spec-folder> <task-id>, e.g. 01-foo 1.2]
---

# Spec Next

Follow `docs/specs/EXECUTION_PROTOCOL.md`. Execute the **NEXT unchecked subtask only, then STOP**.

Target: $ARGUMENTS

- If `$ARGUMENTS` names a spec folder and/or task id, execute that subtask (after checking its
  dependencies and any phase gate). If empty, auto-pick: the lowest-numbered spec under `docs/specs/`
  with unchecked items, first unchecked subtask.
- One subtask per run. Investigate first, implement only this subtask, run the repo's verification
  commands and **show the output**, flip the checkbox(es), append to the `## Progress Log`, commit the
  scoped files, then STOP. Do not start the next subtask.
- If `docs/specs/EXECUTION_PROTOCOL.md` doesn't exist in this repo, fall back to the canonical copy in
  the `kiro-spec-workflow` skill folder and offer to bootstrap the repo.
