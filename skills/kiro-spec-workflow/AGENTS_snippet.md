<!-- Copy the block below into a repo's AGENTS.md (and/or GEMINI.md, .cursorrules, .github/copilot-instructions.md).
     It routes any AI to the spec-driven workflow. The two referenced docs are dropped into docs/specs/ on first use. -->

## Spec-driven workflow (required for non-trivial work)

For any non-trivial feature or system (more than a one-file tweak), follow the spec-driven workflow
before writing implementation code:

1. **Plan** per [`docs/specs/SPEC_WORKFLOW.md`](docs/specs/SPEC_WORKFLOW.md) — produce, in order,
   `requirements.md` (EARS acceptance criteria) → `design.md` → `tasks.md` inside
   `docs/specs/<feature>/`. **STOP for explicit approval after each document** before starting the next.
   Generate the document first; raise open questions as a `## Decisions Needed` block, don't interview first.
2. **Execute** per [`docs/specs/EXECUTION_PROTOCOL.md`](docs/specs/EXECUTION_PROTOCOL.md) — implement
   **one subtask per run**, run the repo's verification commands and show the output, tick the checkbox,
   append to the Progress Log, commit the scoped files, then **STOP**. Never batch subtasks.

Skip for typos, one-line fixes, and pure questions. If reality contradicts the spec, stop and flag it —
update the spec, don't silently diverge.
