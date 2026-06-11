# Branches and merging

A branch in Git is simply a movable pointer to a commit, and the special pointer `HEAD` marks which branch you are currently on. Creating a branch is cheap because it only writes a new pointer, not a copy of your files. Merging combines the work of two branches into one, either by moving a pointer forward or by creating a new commit that ties the histories together.

## Branches are pointers

A branch is a lightweight, movable reference to a particular commit. When you commit on a branch, the branch pointer moves forward to the new commit automatically. This is why branching is fast and common in Git: making a branch creates a tiny pointer, not a duplicate of the project. The default branch is usually called `main`. `HEAD` is the pointer to the branch you currently have checked out, so it tells Git where your next commit will attach.

## Creating and switching

`git branch <name>` creates a new branch pointing at your current commit. `git switch <name>` moves you onto an existing branch, updating your working directory to match it; `git switch -c <name>` creates and switches in one step. (The older `git checkout` does both jobs and more, which is why `switch` was introduced to be clearer.) Switching branches changes which line of work your edits and commits apply to.

## Merging two branches

`git merge <branch>` brings the named branch's commits into your current branch. If your current branch has not advanced since the other branch split off, Git does a "fast-forward": it just moves your branch pointer up to the other one, no new commit needed. If both branches have new commits, Git creates a merge commit with two parents, joining the two histories while preserving both.

## Merge conflicts

A conflict happens when the two branches changed the same lines of the same file in incompatible ways, so Git cannot decide which version wins. Git pauses the merge and marks the conflicting sections in the file with markers showing both versions. You resolve a conflict by editing the file to the version you want, removing the markers, staging it with `git add`, and completing the merge with `git commit`. Conflicts are a normal part of collaboration, not an error you did wrong.
