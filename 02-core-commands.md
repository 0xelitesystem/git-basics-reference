# Core commands

The everyday Git commands map directly onto the three areas: `status` and `diff` show you where things stand, `add` stages changes, `commit` records them, `log` shows history, and `clone`, `pull`, and `push` move commits between your repository and a remote one. A small set of commands covers almost all routine work.

## Seeing where you are

`git status` reports which files are modified, staged, or untracked, and which branch you are on. It is the command you run most, because it tells you the state across all three areas. `git diff` shows the actual line-by-line changes: with no arguments it shows working-directory changes not yet staged, and `git diff --staged` shows what is staged and headed for the next commit. Together they answer "what have I changed and what am I about to commit."

## Recording work

`git add <file>` stages a file's current changes; `git add .` stages everything in the current directory tree. `git commit -m "message"` records the staged changes as a new snapshot with that message. A good message says what changed and why in one line. `git commit -a -m "message"` is a shortcut that stages and commits all already-tracked modified files at once, skipping the separate add, though it ignores brand-new untracked files.

## Reviewing history

`git log` lists commits from newest to oldest, each with its author, date, message, and unique hash. `git log --oneline` condenses each commit to a single line, which is far easier to scan. The commit hash is how you refer to a specific commit in other commands. History is a chain: each commit points back to its parent, and following those links is how Git reconstructs any past state of the project.

## Working with a remote

`git clone <url>` copies an existing remote repository to your machine, including all its history. `git pull` fetches new commits from the remote and merges them into your current branch. `git push` sends your local commits to the remote so others can see them. A remote named `origin` is created automatically by `clone`. These three commands are how Git goes from a local tool to a way teams share a single history.
