# Set up a project

Use this procedure when the user asks to configure a project to use this repository. A request to read or follow shared preferences applies them to the current task; it does not trigger setup.

Follow [workflow.md](./workflow.md), [general conventions](./conventions/general.md), and the target project's applicable instructions. Resolve links in this guide relative to this file's location, including when reading remotely.

## Procedure

1. Identify the target project from the user's request or the current working project. If the target is unclear, ask for its location. Reading or checking out `agent-config` does not make it the target project. Inspect the target's existing instruction files before editing.

2. Create or update the target project's root `AGENTS.md` using the pointer in [project-AGENTS.md](./adapters/project-AGENTS.md).
   - If setup includes tools that read `AGENTS.md` and general project instructions exist only in `CLAUDE.md`, identify those instructions and ask whether to move them into `AGENTS.md`, unless the user has already authorized that migration. This does not apply to setup explicitly limited to Claude Code.
   - If the user agrees, move the general project instructions without changing their meaning and keep Claude-specific instructions in `CLAUDE.md`. Its import in step 3 will load the moved instructions. If the user declines, preserve the existing content and report that those instructions remain outside `AGENTS.md`.
   - Add the pointer above existing project-specific content, preserving that content.
   - Include the project pointer even when user-level shared configuration exists, so other tools and contributors can use the project's configuration independently.
   - Use the adapter's hosted URL by default. Use an absolute local path or a specific revision when requested.
   - If a pointer to this shared configuration already exists, reuse it and preserve its location or revision unless the user asks to change it.
   - Keep shared preferences in this repository; keep project-specific instructions in the target project.

3. Create or update the target project's root `CLAUDE.md` using [project-CLAUDE.md](./adapters/project-CLAUDE.md), which imports the target project's `AGENTS.md`.
   - Add the import above any existing Claude-specific instructions, preserving those instructions.
   - If an existing import or symlink already loads the target's `AGENTS.md`, keep it without adding a duplicate.
   - Configure both project entry files by default. Follow an explicit request to configure only a particular tool.
   - This procedure configures the target project. Change user-level files only when the user requests that setup.

4. Verify the setup.
   - Inspect the diff and confirm that existing instructions were preserved and pointers and imports were not duplicated.
   - If instructions were moved from `CLAUDE.md`, confirm that the general project rules are now in `AGENTS.md` and Claude-specific rules remain in `CLAUDE.md`.
   - Confirm that the Claude import resolves to the target project's `AGENTS.md`.
   - Read the shared entry point and its applicable links using the configured location. Report any file or URL that cannot be retrieved.
   - Summarize the changed files and checks. Distinguish files you read from files confirmed to load automatically in a fresh agent session.

Running setup again should leave correctly configured files unchanged. Follow the shared workflow's commit and push rules.
