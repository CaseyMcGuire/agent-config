# agent-config

Tool-independent instructions for coding agents across projects.

## Use

Point each project's agent instructions to [AGENTS.md](./AGENTS.md), using an absolute path to a local checkout or its raw URL for remote access:

```
https://raw.githubusercontent.com/CaseyMcGuire/agent-config/master/AGENTS.md
```

Use the raw URL rather than the `github.com/.../blob/...` page, which returns the file wrapped in site navigation. Tell the agent to read the entry point and follow its applicable links.

Links within this repository are relative to the document containing them. When reading remotely, resolve them against that document's URL.

Copy-paste entry files for specific tools are in [adapters/](./adapters/README.md).

## Structure

| File | Purpose |
| --- | --- |
| [AGENTS.md](./AGENTS.md) | Entry point, required reading, and precedence. |
| [workflow.md](./workflow.md) | Collaboration, reviewable chunks, implementation order, and Git workflow. |
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
