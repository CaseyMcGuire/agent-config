# Adapters

Copy-paste entry files that point a tool at [AGENTS.md](../AGENTS.md). They contain no preferences; keep preferences in the shared files.

File names deliberately do not match the names tools load automatically (`AGENTS.md`, `CLAUDE.md`), so nothing in this directory is picked up when working in this repository.

| Stub | Copy to | Read by |
| --- | --- | --- |
| [project-AGENTS.md](./project-AGENTS.md) | `<project>/AGENTS.md`, above project-specific content | Tools that load `AGENTS.md`, including Codex. Other tools may require configuration to recognize this filename. |
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

- Without the user-level adapter, add `project-AGENTS.md` above
  the project-specific content in the project's `AGENTS.md`.
  The Claude shim then loads that entry point.

- Verify with `/context`: check that the expected user-level,
  project-level, and directly imported files appear under
  Memory files. Files reached through ordinary Markdown links
  require the agent to read them separately.
