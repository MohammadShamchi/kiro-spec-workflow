---
description: Start or iterate a Kiro-style spec (Requirements → Design → Tasks) for a feature
argument-hint: [feature idea, or blank to resume the in-progress spec]
---

# Spec

Explicit Kiro trigger — load `kiro-spec-workflow` and follow `SPEC_WORKFLOW.md` exactly:
Requirements (EARS) → Design → Tasks, written into `docs/specs/<feature>/`, with a **hard approval
gate after each document** — stop and wait for my explicit approval before the next phase. Generate
the document first; raise open questions in a `## Decisions Needed` block rather than interviewing first.

Feature / instruction: $ARGUMENTS

If `$ARGUMENTS` is empty, resume the spec already in progress (locate the latest `docs/specs/*` folder
and continue the current phase, or ask which feature if ambiguous). Do not write implementation code —
that's `/spec-next` after `tasks.md` is approved.
