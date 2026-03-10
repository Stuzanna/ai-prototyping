---
description: Check and fix markdown formatting issues, using markdownlint-cli2
allowed-tools: Bash(git status*), Bash(npx markdownlint-cli2*)
---

# Markdown Linting

## Pre-flight Check

1. Check for unstaged markdown files: `git status --porcelain | grep '\.md$'`
   - If output contains ` M ` or `??` for .md files:
     - Warn me that unstaged markdown files exist
     - Ask whether to:
       a) Proceed anyway (changes will be made to unstaged files)
       b) Abort so I can commit/stage files first
   - If no unstaged .md files or I choose to proceed: continue to next step

## Run Linter

1. Execute linter with auto-fix: `npx markdownlint-cli2 --fix`
   - Uses config from `.markdownlint-cli2.jsonc` (e.g. excluding files)
   - This will automatically fix issues like:
     - MD047: Files must end with a single newline
     - MD012: Multiple consecutive blank lines
     - Other standard markdown formatting rules
2. Report the results:
   - If no issues found: confirm all files pass
   - If issues fixed: list what was corrected
   - If issues can't be auto-fixed: show errors for manual review
