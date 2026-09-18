### 1. What did the rejected push error message tell you, and why did it happen?
The `! [rejected] (fetch first)` error indicated that the remote branch had new commits that I did not have locally. It happened because another developer (the alternate clone) pushed changes to the shared remote repository while I was working locally, causing our branch histories to diverge. 

### 2. What's the actual difference between how you resolved Task 3 (merge) vs Task 4 (rebase)?
In Task 3, `git merge` preserved the exact chronological history by creating a brand-new "merge commit" that tied both diverged branches back together. In Task 4, `git rebase` temporarily set aside my local commit, pulled down the remote changes, and then re-applied my local commit directly on top of the updated remote history, resulting in a clean, linear timeline without an extra merge commit.

### 3. What one habit would have avoided both rejected pushes in this lab?
Running `git pull` (or `git fetch` and checking status) immediately before starting new work, and again immediately before attempting to push, ensures the local branch is always synced with the remote first.

### 4. Which approach - merge or rebase - would you default to on a shared team branch, and why?
For syncing everyday changes on a shared feature branch, I would default to a rebase (`git pull --rebase`) to prevent the Git history from becoming cluttered with unnecessary "merged branch" commits. However, when a feature branch is fully completed and ready to be integrated into `main`, a standard `merge` is preferable to preserve the context of the feature as a grouped set of commits.