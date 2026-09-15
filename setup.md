# Set up a project

Use this procedure when the user asks to use this configuration for a project. Requests such as "use this repo," "use this configuration," and "set up this project" all mean persistent project setup by default. Complete the setup without asking the user to confirm that interpretation.

If the user explicitly requests use "for this task only" or "for this session only," read and follow the shared preferences without changing the project's instruction files or installing skills. Reading this repository for review or loading an existing configuration pointer during ordinary work does not trigger setup.

Follow [workflow.md](./workflow.md), [general conventions](./conventions/general.md), and the target project's applicable instructions. Resolve links in this guide relative to this file's location, including when reading remotely.

## Procedure

1. Identify the target project from the user's request or the current working project. If the target is unclear, ask for its location. Reading or checking out `agent-config` does not make it the target project. Inspect the target's existing instruction files before editing.

2. Create or update the target project's root `AGENTS.md` using the pointer in [project-AGENTS.md](./adapters/project-AGENTS.md).
   - If setup includes tools that read `AGENTS.md` and general project instructions exist only in `CLAUDE.md`, move those instructions into `AGENTS.md` as part of setup, without a separate confirmation. Skip this migration when setup is explicitly limited to Claude Code or the user asks to keep those instructions in place.
   - Move project-wide guidance such as build and test commands, architecture, and coding conventions without changing its meaning. Keep instructions about Claude-specific tools and commands in `CLAUDE.md`. Preserve the instructions' scope and link targets; the import in step 3 will let Claude read the moved rules.
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

4. Install the skills in [skills/](./skills/) for the selected tools, following the [skill installation guide](./adapters/README.md#shared-skill-installation).

5. Verify the setup.
   - Inspect the diff and confirm that existing instructions were preserved and pointers and imports were not duplicated.
   - If instructions were moved from `CLAUDE.md`, confirm that the general project rules are now in `AGENTS.md` and Claude-specific rules remain in `CLAUDE.md`.
   - Confirm that the Claude import resolves to the target project's `AGENTS.md`.
   - Confirm each installed skill is readable and discoverable by the selected tools. Check native discovery in fresh sessions when available.
   - Read the shared entry point and its applicable links using the configured location. Report any file or URL that cannot be retrieved.
   - Summarize the changed files and checks. Distinguish file validation, native skill discovery, and any actual workflow execution tested in a fresh agent session.

Running setup again should leave correctly configured files unchanged. Follow the shared workflow's commit and push rules.
