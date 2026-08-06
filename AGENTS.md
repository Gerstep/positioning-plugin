# positioning-plugin

This repo ships one Agent Skill: `skills/positioning/`. It is also
discoverable at `.agents/skills/` (a symlink) so Codex finds it when working
inside this repo.

To use the skill here: `/positioning` in Claude Code or Cowork, `$positioning`
in Codex.

To work on the skill:

- The entry point is `skills/positioning/SKILL.md`. Keep it lean; details
  belong in `references/` (progressive disclosure), output templates in
  `assets/`.
- SKILL.md frontmatter must stay within the Agent Skills spec fields (`name`,
  `description`, `license`, `compatibility`, `metadata`, `allowed-tools`) so
  the skill stays portable across Claude Code, Cowork, Codex, and claude.ai
  uploads. `metadata` values must be strings.
- Do not hard-depend on any harness-specific tool. Interactive question tools,
  subagents, and web search are all optional with plain-text fallbacks spelled
  out in SKILL.md.
- Bump `version` in `.claude-plugin/plugin.json`, `marketplace.json`, and the
  SKILL.md `metadata` together.
