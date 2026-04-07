# /kudoc-push

Safely commit and push all pending changes to kudocai master.

Steps:
1. Run `git pull --rebase kudocai master` first to avoid push rejections
2. Run `git status` to identify changed/untracked files (never add .DS_Store)
3. Stage relevant files: `git add <files>` — be specific, not `git add -A`
4. Commit with the message provided as the argument to this command (e.g. `/kudoc-push "Add new paper"`)
   - If no message is provided, ask the user for one before committing
5. Run `git push kudocai master`
6. Confirm success and report the commit hash

If the argument is provided as $ARGUMENTS, use it as the commit message directly.
