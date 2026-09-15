# Adapters

Copy-paste entry files that point a tool at [AGENTS.md](../AGENTS.md). They contain no preferences; keep preferences in the shared files.

File names deliberately do not match the names tools load automatically (`AGENTS.md`, `CLAUDE.md`), so nothing in this directory is picked up when working in this repository.

| Stub | Copy to | Read by |
| --- | --- | --- |
| [project-AGENTS.md](./project-AGENTS.md) | `<project>/AGENTS.md`, above project-specific content | Tools supporting `AGENTS.md`; see [agents.md](https://agents.md/) for the ecosystem list and tool-specific setup requirements. |
| [project-CLAUDE.md](./project-CLAUDE.md) | `<project>/CLAUDE.md` | Claude Code, which reads `CLAUDE.md` rather than `AGENTS.md`. |
| [user-CLAUDE.md](./user-CLAUDE.md) | `~/.claude/CLAUDE.md` | Claude Code, in every project on the machine. |

Replace the hosted URL or `~/src/agent-config` with the location of your checkout.

## Plugin setup

Plugin installation is optional for skill-picker and command integration.
Agents can discover and follow skills remotely through the shared-config
pointer and [skill catalog](../AGENTS.md#skill-catalog), without local skill files.

Install the `agent-config` plugin once in each tool. It provides all included
skills as native commands; no separate skill installation is needed. Both
tool-specific manifests use this repository's canonical `skills/` directory,
including supporting files. The tool manages its installed copy.

For Codex:

```sh
codex plugin marketplace add CaseyMcGuire/agent-config --ref master
codex plugin add agent-config@agent-config
```

For Claude Code:

```sh
claude plugin marketplace add CaseyMcGuire/agent-config
claude plugin install agent-config@agent-config --scope user
```

These commands make skills available across projects. Use the user's selected
scope when they request something narrower. See the [Codex plugin guide](https://developers.openai.com/plugins/build/plugins)
and [Claude plugin guide](https://code.claude.com/docs/en/plugins) for native
installation and discovery behavior.

The marketplace source is the Git repository, not a raw `marketplace.json`
URL: each catalog's `./` plugin source resolves to its repository root. When a
specific revision is requested, preserve that revision in the marketplace
source. For local testing before publishing, replace the GitHub source in the
marketplace-add command with this checkout's absolute path. A local
marketplace follows the checkout; it does not fetch GitHub.

After installation, start a fresh session and check native discovery:
`$agent-config:feature-workflow` in Codex and `/agent-config:feature-workflow`
in Claude Code. Check that the plugin's skill files match the configured source. The
shared-config pointer still supplies coding conventions; installing the plugin
does not change when a skill's workflow should be used.

### Updating the plugin

Release skill additions, changes, and removals by updating the canonical
`skills/` directory and bumping the version in both plugin manifests together.
Do not edit installed caches. After publishing the release, refresh with:

```sh
codex plugin marketplace upgrade agent-config
codex plugin add agent-config@agent-config
claude plugin marketplace update agent-config
claude plugin update agent-config@agent-config
```

Start a fresh session after updating. In Claude Code, `/reload-plugins` can
also refresh skills in the current session. Enable automatic updates for this
marketplace through `/plugin` → Marketplaces → agent-config → Enable
auto-update if wanted. Claude's background update can run after startup, with
a delay of up to ten minutes; updated skills then need a reload or another
launch. See [Claude's update behavior](https://code.claude.com/docs/en/discover-plugins#configure-auto-updates).

Native plugin installation makes the installed version available at startup.
It does not promise that every launch fetches the latest GitHub revision before
the first prompt. Verify update behavior separately from initial discovery.

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
