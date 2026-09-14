# Adapters

Copy-paste entry files that point a tool at [AGENTS.md](../AGENTS.md). They contain no preferences; keep preferences in the shared files.

File names deliberately do not match the names tools load automatically (`AGENTS.md`, `CLAUDE.md`), so nothing in this directory is picked up when working in this repository.

| Stub | Copy to | Read by |
| --- | --- | --- |
| [project-AGENTS.md](./project-AGENTS.md) | `<project>/AGENTS.md`, above project-specific content | Tools that read `AGENTS.md` natively: Codex, Cursor, GitHub Copilot, Gemini CLI, Windsurf, Aider, Zed, and others. |
| [project-CLAUDE.md](./project-CLAUDE.md) | `<project>/CLAUDE.md` | Claude Code, which reads `CLAUDE.md` rather than `AGENTS.md`. |
| [user-CLAUDE.md](./user-CLAUDE.md) | `~/.claude/CLAUDE.md` | Claude Code, in every project on the machine. |

Replace the hosted URL or `~/src/agent-config` with the location of your checkout.

## Choosing a route for Claude Code

- Use `user-CLAUDE.md` on your own machine. Imports in user-scope files load without the external-import approval dialog, and the always-read files are in context at launch.
- Use `project-CLAUDE.md` in repositories where other people's tools also need the shared preferences. Add Claude-specific instructions below the import.
- Do not use both in one project; the shared files would load twice.
- Verify with `/context`. The imported files should appear under Memory files.
