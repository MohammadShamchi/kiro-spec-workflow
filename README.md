# Kiro spec workflow for Claude Code

Flow: Requirements (EARS) -> Design -> Tasks -> Execute. Hard approval gate after each document.

Install:
  cp -R skills/kiro-spec-workflow ~/.claude/skills/
  cp commands/*.md ~/.claude/commands/

Use: type /spec <feature> in Claude Code, then /spec-next to run one task at a time.
Specs are written to docs/specs/<feature>/.
Edit SKILL.md to replace the author's name and trigger phrases with yours.
