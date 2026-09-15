# agent-config

Tool-independent instructions for coding agents across projects.

## Use

Open the target project in Claude Code or Codex and give it this prompt:

```text
Set up this project to use:
https://raw.githubusercontent.com/CaseyMcGuire/agent-config/master/AGENTS.md

Follow its linked setup instructions for persistent use. Add a shared-config
pointer to the project's AGENTS.md and ensure CLAUDE.md imports @AGENTS.md.
Preserve existing instructions and reuse equivalent pointers or imports.
Read skills remotely without installing them locally.
Verify that the saved project instruction files lead to the shared skill catalog.
```

Saving the pointer in the target project's instructions lets future sessions
find the remote catalog. The skill files themselves stay remote.

A request to use this configuration, including "use this repo," means persistent project setup by default. Read [setup.md](./setup.md) and follow its instructions in the target project. The agent creates or updates the project's instruction files, preserving existing guidance and avoiding duplicate pointers or imports. Moving general project rules from `CLAUDE.md` into `AGENTS.md` is part of setup and does not require a separate confirmation; Claude-specific instructions stay in `CLAUDE.md`.

For temporary use, say "Use this configuration for this task only" or "for this session only." The agent then follows the shared preferences without changing the project's instruction files or installing skills. Loading an existing configuration pointer during ordinary work does not trigger setup.

For manual setup, point each project's agent instructions to [AGENTS.md](./AGENTS.md), using an absolute path to a local checkout or its raw URL for remote access:

```
https://raw.githubusercontent.com/CaseyMcGuire/agent-config/master/AGENTS.md
```

Use the raw URL rather than the `github.com/.../blob/...` page, which returns the file wrapped in site navigation. Tell the agent to read the entry point and follow its applicable links.

The same pointer exposes the [skill catalog](./AGENTS.md#skill-catalog). Agents
read and follow relevant skills remotely, or when requested by name, without
copying, cloning, symlinking, or installing skill files locally. The full
instructions stay in each skill's canonical `SKILL.md`.

Links within this repository are relative to the document containing them. When reading remotely, resolve them against that document's URL at every step, including supporting references linked from a skill. Report retrieval failures instead of silently skipping instructions.

[Native skill installation](./adapters/README.md#shared-skill-installation) is
optional for users who want skill-picker and command integration.

Copy-paste entry files for specific tools are in [adapters/](./adapters/README.md).

## Structure

| File | Purpose |
| --- | --- |
| [AGENTS.md](./AGENTS.md) | Entry point, skill catalog, required reading, and precedence. |
| [setup.md](./setup.md) | Agent instructions for configuring a target project. |
| [workflow.md](./workflow.md) | Task scope, skill selection, and Git workflow. |
| [skills/feature-workflow/SKILL.md](./skills/feature-workflow/SKILL.md) | Shared feature planning, implementation, and review procedure. |
| [conventions/general.md](./conventions/general.md) | General coding conventions and validation. |
| [conventions/language/java.md](./conventions/language/java.md) | Java conventions. |
| [conventions/language/graphql.md](./conventions/language/graphql.md) | GraphQL conventions and a mutation response example. |
| [conventions/language/kotlin.md](./conventions/language/kotlin.md) | Kotlin placeholder; no established conventions yet. |
| [conventions/language/typescript.md](./conventions/language/typescript.md) | TypeScript placeholder; no established conventions yet. |
| [conventions/libraries/react/README.md](./conventions/libraries/react/README.md) | React conventions. |
| [conventions/libraries/react/stylex.md](./conventions/libraries/react/stylex.md) | StyleX conventions. |
| [conventions/libraries/react/relay.md](./conventions/libraries/react/relay.md) | Relay conventions. |
| [adapters/README.md](./adapters/README.md) | Per-tool entry file stubs that point at the entry point. |

## Maintenance

- Keep each preference in the file for its category.
- Put language files in `conventions/language/` and library files in `conventions/libraries/`, and link them from the entry point and this README.
- Record only established preferences. Mark files without conventions as placeholders.
- Keep project-specific build commands, architecture, dependencies, and database rules in the relevant project's instructions.
- Keep adapter stubs free of preferences. They only point a tool at the entry point.
- Keep each skill's instructions in `skills/<skill-name>/SKILL.md`, with its
  name, purpose, and canonical link in the `AGENTS.md` catalog. Link supporting
  references instead of duplicating instructions. Native skill directories in
  this repository link to the same canonical source.
