# /kudoc-sync

Pull the latest from the canonical remote and report status before doing any work.

Steps:
1. Run `git pull kudocai master`
2. Run `git status`
3. Report what changed (files updated from remote, any local untracked files to be aware of)
4. If there are merge conflicts, stop and describe them clearly for the user to resolve
