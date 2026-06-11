# Undoing changes

Git gives you different tools for undoing depending on what you want to undo and whether the change is shared: `restore` discards uncommitted edits, `reset` moves your branch pointer and unstages or removes commits, and `revert` makes a new commit that cancels an old one. Knowing which one to reach for keeps you from losing work.

## Discarding uncommitted work

To throw away changes in your working directory and go back to the last committed version of a file, use `git restore <file>`. To unstage a file you added but have not committed (keeping the edits, just removing them from the staging area), use `git restore --staged <file>`. These handle the common case of "I made a mess in my working directory, let me start that file over." They only touch uncommitted state, so they cannot lose committed history.

## Resetting commits

`git reset` moves your current branch pointer to an earlier commit. `git reset --soft <commit>` moves the pointer but keeps your changes staged; `git reset --mixed` (the default) keeps them in the working directory unstaged; `git reset --hard` discards them entirely to match the target commit. Soft and mixed are safe ways to redo recent commits. Hard reset permanently throws away uncommitted work, so use it deliberately. Reset rewrites where the branch points, so avoid it on shared commits.

## Reverting safely

`git revert <commit>` is the safe way to undo a commit that has already been shared. Instead of removing the commit, it creates a new commit that applies the inverse of the target's changes, cancelling its effect while leaving history intact. Because it adds rather than rewrites, revert never causes the problems that resetting shared commits does. Reach for revert whenever the bad commit is already pushed and others may have it.

## Recovering lost work

If you reset or rebase and think you lost commits, they are usually still findable. `git reflog` records where `HEAD` has pointed over time, including commits that are no longer on any branch. Find the lost commit's hash in the reflog and you can return to it with `git reset` or by creating a branch there. Git rarely deletes commits immediately, so "lost" work after a bad reset is often just one reflog lookup away from recovery.
