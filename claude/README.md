# Claude Commands

## Create commands directory if it doesn't exist
```bash
mkdir -p .claude/commands
```

## Copy command files
```bash
cp foo.md .claude/commands/foo.md
```
## Commands

`upsert-pr` is my own one, `pr` is an example for preparing a PR I used as a base.

## allowed-tools

Note I hit issues with nested commands within brackets in the allowed-tools, it doesn't seem to like this, even if you explicitly allow the full command. Suggest refactoring into two commands or pipe.

Note you need to add to `.claude/settings.local.json` as well to avoid the prompt.
