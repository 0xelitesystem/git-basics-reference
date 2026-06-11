# The .gitignore file

A `.gitignore` file tells Git which files and folders to leave untracked, so they never get staged, committed, or shown as changes. It exists to keep generated files, dependencies, secrets, and machine-specific clutter out of your repository, leaving history clean and focused on the source you actually wrote.

## What it does

`.gitignore` is a plain text file, usually at the root of your repository, listing patterns of paths Git should ignore. Any file matching a pattern is treated as if it is not there: it will not appear in `git status` as untracked and will not be added by `git add .`. This keeps you from accidentally committing things that do not belong in version control, which is easy to do when staging everything at once.

## What to ignore

Common things to ignore are build outputs (`dist/`, `build/`), installed dependencies (`node_modules/`), editor and OS files (`.vscode/`, `.DS_Store`, `Thumbs.db`), logs (`*.log`), and anything secret (`.env`, key files). The rule of thumb: ignore anything that can be regenerated, anything specific to one person's machine, and anything sensitive. Source code and the project's own configuration belong in the repository; everything downstream of them usually does not.

## Pattern syntax

Patterns are matched against file paths. A bare name like `secret.txt` matches that file anywhere; a trailing slash like `logs/` matches a directory and its contents; an asterisk like `*.log` matches any file with that extension; and a leading slash like `/build` anchors the pattern to the repository root. A line starting with `!` re-includes something a previous pattern excluded. Comments start with `#`. These few rules cover almost every ignore you will ever write.

## The already-tracked catch

`.gitignore` only stops Git from tracking files it is not already tracking. If you committed a file and then add it to `.gitignore`, Git keeps tracking it, because ignore rules do not apply to already-tracked files. To fix this, remove it from tracking while keeping it on disk with `git rm --cached <file>`, then commit. This catch surprises people who add a secret to `.gitignore` after already committing it; the ignore alone does not remove the committed copy from history.
