# Shared agent instructions

Apply these shared preferences as defaults. Explicit project instructions may override them.

## Load only relevant instructions

- Always apply [workflow.md](./workflow.md) and [conventions/general.md](./conventions/general.md), reading them if their contents are not already available in context.
- Load language and library conventions only when relevant to the current task. A technology's presence elsewhere in the project does not make its conventions relevant to every task.
- Determine relevance from the request, project instructions, and affected code. Inspect dependency manifests only when needed.
- Include conventions for technologies the task introduces, even if the project does not use them yet.
- Do not preload every linked file or the entire conventions directory. Read additional guides as they become relevant during the task.
- Reuse instructions already available in context. Read them again only if they changed or their contents are no longer available.

## Task-specific instructions

- When the user asks to use this configuration for a project, including "use this repo," follow [setup.md](./setup.md) for persistent setup unless the user explicitly requests task-only or session-only use. Loading an existing configuration pointer does not trigger setup.
- For Java work, also read [conventions/language/java.md](./conventions/language/java.md).
- For GraphQL work, also read [conventions/language/graphql.md](./conventions/language/graphql.md).
- For Kotlin work, also read [conventions/language/kotlin.md](./conventions/language/kotlin.md).
- For TypeScript work, also read [conventions/language/typescript.md](./conventions/language/typescript.md).
- For React work, also read [conventions/libraries/react/README.md](./conventions/libraries/react/README.md).
- For StyleX work, also read [conventions/libraries/react/stylex.md](./conventions/libraries/react/stylex.md).
- For Relay work, also read [conventions/libraries/react/relay.md](./conventions/libraries/react/relay.md).
- Report any referenced instructions that cannot be retrieved, identifying the unavailable file or URL.

Resolve these links relative to this file's location, including when reading this repository remotely.
