---
description: Prepare a pull request from the current branch, or update an existing PR's description
allowed-tools: Bash(git status --porcelain), Bash(git branch --show-current), Bash(gh repo view --json*), Bash(gh pr list*), Bash(git diff*...HEAD), Bash(git log*..HEAD*), Bash(gh pr create --title*), Bash(gh pr edit --body*), Bash(gh pr view*)
---

# Pull Request Preparation

## Pre-flight Checks

1. Check for uncommitted changes: `git status --porcelain`
   - If changes exist, warn me and ask whether to proceed or abort
2. Identify the base branch: `gh repo view --json defaultBranchRef --jq '.defaultBranchRef.name'`

## Check for Existing PR

Don't ask for permissions here.
1. Get current branch: `git branch --show-current`
2. Check for PR: `gh pr list --head <current-branch> --json number --jq 'length'`
   - Returns `0` = No PR exists, proceed to create flow
   - Returns `1` or more = PR exists, proceed to update flow

## If No PR Exists

1. Review changes: `git diff <base>...HEAD`
2. Review commit history: `git log <base>..HEAD --oneline`
3. Generate a PR description including:
   - **Summary**: What changed (high-level)
   - **Changes**: Key modifications (be specific)
   - **Why**: Motivation or context
   - **Testing**: How this was tested (if applicable)
4. Present the proposed title and description for my review
5. **Wait for my explicit approval before creating**
   - If approved: `gh pr create --title "..." --body "..."`
   - If edits requested: incorporate feedback and present again

## If PR Already Exists

1. Display the current PR description
2. Review commits since PR was opened: `git log <base>..HEAD --oneline`
3. Review the diff: `git diff <base>...HEAD`
4. Propose updated description, showing what changed from the original
5. **Wait for my explicit approval before updating**
   - If approved: `gh pr edit --body "..."`
   - If denied or edits requested: incorporate feedback or stop

Never create or update a PR without my confirmation.