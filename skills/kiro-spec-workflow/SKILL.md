---
name: kiro-spec-workflow
description: Load when Mohammad explicitly triggers Kiro spec discipline — follow spec, follow kiro, kiro model, spec-driven, use the spec workflow, ship with spec, or runs /spec or /spec-next. Runs Requirements (EARS) → Design → Tasks → Execute into docs/specs/<feature>/ (or .kiro/specs/) with HARD approval gates. Do NOT load for informal "let's build X", quick plan, typos, one-line fixes, or pure questions unless he picks Kiro after you ask. Supersedes spec-before-code and superpowers:brainstorming only when this skill is active.
---

# Kiro Spec Workflow

Opt-in skill — not every build. Read `SPEC_WORKFLOW.md` in this folder for full rules. `~/.claude/CLAUDE.md` and Cursor `mohammad-core` / `mohammad-kiro-spec` use the same trigger model.

## When this fires (explicit only)

**Triggers:**
- Phrases: follow spec, follow kiro, kiro model, spec-driven, use the spec workflow, ship with spec
- Commands: `/spec`, `/spec-next`
- He picks **Kiro** after you ask "Kiro spec or quick plan?"

**Do not fire** for informal "let's build X", **quick plan**, typos, one-line fixes, renames, debugging, or pure questions. **Do not infer** from multi-file or large scope alone.

When active, **supersedes** `spec-before-code` and `superpowers:brainstorming` — do not also run those.

## The flow (enforce the gates)

Read `SPEC_WORKFLOW.md` for the full rules, then:

1. **Requirements.** Derive a kebab-case feature name. Write `docs/specs/<feature>/requirements.md`
   from `templates/requirements.md` — fill Current State, Goal, Investigation Findings, EARS
   requirements (`R<n>.<m>` ids), Non-Functional, Out of Scope. Put open questions in
   `## Decisions Needed` with recommended defaults in bold. **Generate the doc first, ask second.**
   Then **STOP** and ask: "Requirements drafted at `<path>`. Approve to move to Design, or tell me what to change?"
2. **Design** (only after explicit approval). Write `design.md` from `templates/design.md` — Overview,
   Architecture, Components & Interfaces, Data Models, Error Handling, Verification Strategy (+ Reuse
   Map / Risks / Files Changed). Research inline. **STOP** for approval.
3. **Tasks** (only after explicit approval). Write `tasks.md` from `templates/tasks.md` — two-level
   tree, each top task citing `(R…)`, plus Dependency/Execution Order, Verification Checklist,
   Definition of Done, Progress Log. Respect the banned-task list. **STOP** for approval.
4. **Execute** (only after explicit approval). Switch to `EXECUTION_PROTOCOL.md`: one subtask per run,
   verify, tick the box, log, commit, STOP. This is what `/spec-next` triggers.

**Gate discipline:** explicit "approved"/"yes"/"continue" only — silence is not approval. After any
edit, re-request approval. The machine is bidirectional: honor "go back to requirements/design".
Never write the next document or any implementation code before the current phase is approved.

## File locations

- Default `docs/specs/<feature>/`. If the repo has no `docs/`, use `notes/specs/<feature>/` (draft)
  and offer to promote to `docs/specs/` once agreed.
- Multi-phase work: number folders (`00-…`, `01-…`) and add a `docs/specs/README.md` index with phase
  order, dependencies, and locked decisions.

## Per-repo bootstrap (do this once per repo, silently, on first spec)

So the workflow is portable and other AIs follow it, on the first run in a repo that lacks
`docs/specs/SPEC_WORKFLOW.md`:

1. Copy each of `SPEC_WORKFLOW.md` and `EXECUTION_PROTOCOL.md` from this skill folder into the repo's
   `docs/specs/` (create the dir) **only if that file does not already exist there** — never overwrite
   a repo's existing copy (some repos, e.g. meetyourmind, ship a tailored `EXECUTION_PROTOCOL.md`;
   keep it). These become the repo's canonical, committed copies.
2. If the repo's `AGENTS.md` doesn't already route to the spec workflow, append the contents of
   `AGENTS_snippet.md` (this folder) to it, creating `AGENTS.md` if absent. Routes Codex / Gemini /
   Cursor / Kiro to the same workflow.
3. If `docs/README.md` exists and lacks a specs row, add one pointing to `docs/specs/`.
4. Mention the bootstrap in one line; don't make a production of it.

Bootstrap is idempotent: anything already present (as in the meetyourmind repo, which has
`docs/specs/` + `EXECUTION_PROTOCOL.md`) is left untouched — just use it.

## Bundled files

- `SPEC_WORKFLOW.md` — canonical authoring/gating rules (read this).
- `EXECUTION_PROTOCOL.md` — one-subtask-per-run executor.
- `templates/{requirements,design,tasks}.md` — fill-in templates.
- `AGENTS_snippet.md` — the AGENTS.md pointer block for bootstrap.

## Output discipline

- No preamble ("Great question!"). Direct and concise — match my global style.
- Don't announce internal phase-tracking mechanics at length; just do the phase and stop at the gate.
- If a request is genuinely trivial and this fired by mistake, say so in one line and proceed without ceremony.
