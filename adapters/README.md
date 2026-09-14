# Adapters

Copy-paste entry files that point a tool at [AGENTS.md](../AGENTS.md). They contain no preferences; keep preferences in the shared files.

File names deliberately do not match the names tools load automatically (`AGENTS.md`, `CLAUDE.md`), so nothing in this directory is picked up when working in this repository.

| Stub | Copy to | Read by |
| --- | --- | --- |
| [project-AGENTS.md](./project-AGENTS.md) | `<project>/AGENTS.md`, above project-specific content | Tools supporting `AGENTS.md`; see [agents.md](https://agents.md/) for the ecosystem list and tool-specific setup requirements. |
| [project-CLAUDE.md](./project-CLAUDE.md) | `<project>/CLAUDE.md` | Claude Code, which reads `CLAUDE.md` rather than `AGENTS.md`. |
| [user-CLAUDE.md](./user-CLAUDE.md) | `~/.claude/CLAUDE.md` | Claude Code, in every project on the machine. |

Replace the hosted URL or `~/src/agent-config` with the location of your checkout.

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
