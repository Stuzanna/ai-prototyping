# Memory

Richer content on, and credit to, [gh:luongnv89/claude-howto](https://github.com/luongnv89/claude-howto/blob/main/README.md#L6-L7).

Memory is for context windows across sessions:

* Sharing standards.
* Store dev preferences.
* Import external docs.
* VCS memory as part of the project.

## /init

Set up memory with a CLAUDE.md file with project information.

Typically at ./CLAUDE.md, or ./.claude. The foundation for context persistence.

Good for starting project, establishing standards, creating a doc about codebase.

## Quick memory updates

```bash
# use kebab-case for naming
# Run npm test before each commit
```

Recognised as memory update, it asks which memory file to update, project or personal.

Alternatively:

```bash
# remember this
Use semantic versioning

# add to memory
Schema upgrades
```

You can also do detailed edit with `/memory`.

### Memory imports

`@path/to/file` to include external content. Relative or absolute paths.

```md
# Project Documentation
See @README.md for project overview
See @package.json for available npm commands
See @docs/architecture.md for system design

# Import from home directory using absolute path
@~/.claude/my-project-instructions.md
```

## Hierarchy

Higher levels having precedence.

1. Managed policy, org-wide, in the app library, or /etc for claude.
1. Project memory, team context, usually repo root or `./claude/`.
   1. Note this is where memory imports from files will be.
1. Project-level-rules, modular, `.claude/rules/*.md`.
1. User memory, personal preferences for all projects, `~/.claude/CLAUDE.md`.
1. User-level rules, personal rules (all projects) `~/.claude/rules/*.md`.
1. Local project memory - Personal project-specific preferences, `./CLAUDE.local.md`.
1. Auto memory, Claude's automatic notes and learnings, `~/.claude/projects/<project>/memory/`

## Modular rules

Skills live in /commands, rules are to do with memory for persisting context.
Similar to the memory update examples above.

You can have project rules and user rules, subdirectories supported as they're discovered recursively.
Personal defaults overridden by project.

Can be locked to specific paths, with glob pattern examples.

## Additional directories

The --add-dir flag allows Claude Code to load CLAUDE.md files from additional directories.
 This is useful for monorepos or multi-project setups where context from other directories is relevant.

To enable this feature, set the environment variable:
`CLAUDE_CODE_ADDITIONAL_DIRECTORIES_CLAUDE_MD=1`

Then launch Claude Code with the flag:
`claude --add-dir /path/to/other/project`

Claude will load CLAUDE.md from the specified additional directory alongside the memory files from your current working directory.
