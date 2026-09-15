# Adapters

Copy-paste entry files that point a tool at [AGENTS.md](../AGENTS.md). They contain no preferences; keep preferences in the shared files.

File names deliberately do not match the names tools load automatically (`AGENTS.md`, `CLAUDE.md`), so nothing in this directory is picked up when working in this repository.

| Stub | Copy to | Read by |
| --- | --- | --- |
| [project-AGENTS.md](./project-AGENTS.md) | `<project>/AGENTS.md`, above project-specific content | Tools supporting `AGENTS.md`; see [agents.md](https://agents.md/) for the ecosystem list and tool-specific setup requirements. |
| [project-CLAUDE.md](./project-CLAUDE.md) | `<project>/CLAUDE.md` | Claude Code, which reads `CLAUDE.md` rather than `AGENTS.md`. |
| [user-CLAUDE.md](./user-CLAUDE.md) | `~/.claude/CLAUDE.md` | Claude Code, in every project on the machine. |

Replace the hosted URL or `~/src/agent-config` with the location of your checkout.

## Shared skill installation

Native installation is optional for skill-picker and command integration.
Agents can discover and follow skills remotely through the shared-config
pointer and [skill catalog](../AGENTS.md#skill-catalog), without local skill files.

The portable [feature-workflow skill](../skills/feature-workflow/SKILL.md) uses
standard `name` and `description` frontmatter. Its instructions are shared by
both tools; it does not require a plugin or tool-specific execution settings.

| Tool | Project discovery path | Explicit invocation |
| --- | --- | --- |
| Codex | `.agents/skills/<skill-name>/SKILL.md` | `$<skill-name>` |
| Claude Code | `.claude/skills/<skill-name>/SKILL.md` | `/<skill-name>` |

In this repository, both skill directories are relative symlinks to
`skills/feature-workflow`. Both tools support symlinked skill directories:
[Codex documentation](https://learn.chatgpt.com/docs/build-skills#where-to-save-skills)
and [Claude Code documentation](https://code.claude.com/docs/en/skills#choose-where-skills-load).

When native installation is requested during [project setup](../setup.md), use
the [catalog](../AGENTS.md#skill-catalog) to locate canonical skill directories.
Copy each complete directory to the selected tool's project discovery path,
using the same configuration source and revision as the entry point. When configuring
both tools, copy into `.agents/skills/<skill-name>` and link
`.claude/skills/<skill-name>` to `../../.agents/skills/<skill-name>`.
Keep the installed files and relative links in the project's version control.

Preserve this repository's existing links to its canonical skill directories.
Reuse correct links or identical copies, refresh older installed copies, and
report conflicting unrelated skills without overwriting them.

The shared pointer makes skill instructions available for agents to read;
native installation also registers them in the tool's skill picker. When
installing from a hosted source, fetch canonical files from `skills/`, since
raw Git symlink entries contain only link targets.

For user-level installation when requested, copy or link the canonical skill
directory to `~/.agents/skills/<skill-name>` for Codex and
`~/.claude/skills/<skill-name>` for Claude Code. This makes it available
across projects on that machine. Avoid installing a second copy when that
scope already provides the skill you want to use.

Start a fresh session after creating a discovery directory for the first time
and check `/skills` for the installed skills.

## Setting up Claude Code

- Copy `user-CLAUDE.md` to `~/.claude/CLAUDE.md` to load shared
  preferences from a local checkout across your projects.
  Replace `~/src/agent-config` with your checkout's path.

- In projects whose instructions live in `AGENTS.md`, copy
  `project-CLAUDE.md` to the project's `CLAUDE.md`. This imports
  the project's instructions. Ensure that `AGENTS.md` exists.

- These adapters can be used together: the user-level file loads
  shared preferences, while the project-level file loads project
  instructions. A project pointer to the same shared preferences
  may cause additional reads; that is not a reason to omit the
  project's instructions.

- Add `project-AGENTS.md` above project-specific content in the
  project's `AGENTS.md`, even when a user-level adapter exists.
  This keeps the project's shared preferences available to other
  tools and contributors independently of your user-level
  configuration. The Claude shim also loads that entry point.

- If general project instructions exist only in `CLAUDE.md`, follow
  [setup.md](../setup.md) to move them into `AGENTS.md` as part of
  setup for other tools, without a separate confirmation. Keep
  Claude-specific instructions in `CLAUDE.md`.

- Verify with `/context`: check that the expected user-level,
  project-level, and directly imported files appear under
  Memory files. Files reached through ordinary Markdown links
  require the agent to read them separately.
