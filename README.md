# Git Basics

A plain-language reference on the fundamentals of Git: the three areas your work moves through, the core commands you use every day, how branches and merging work, the difference between rebase and merge, how to undo changes safely, and what `.gitignore` is for. It is aimed at someone who wants a correct mental model rather than a memorized list of commands.

## The core idea

Git tracks your project as a series of snapshots called commits, and your work moves through three areas to become one: the working directory where you edit, the staging area where you assemble the next commit, and the repository where commits are stored permanently. You edit files, stage the changes you want to record, then commit them as a snapshot with a message. Branches are just movable pointers to commits, which is what makes branching and merging cheap and central to how Git is used.

## What is inside

- `01-the-three-areas.md` working directory, staging area, and commits.
- `02-core-commands.md` the everyday commands and what each one does.
- `03-branches-and-merging.md` branches as pointers and how merges combine them.
- `04-rebase-vs-merge.md` two ways to integrate work and when to use each.
- `05-undoing-changes.md` checkout, restore, reset, and revert without losing work.
- `06-gitignore.md` keeping files out of version control.

## The stance

This reference treats Git as a snapshot system with a few clear rules, not a pile of magic incantations. Once you understand the three areas and that branches are pointers, most commands stop being mysterious. The goal is a model you can reason from, so unfamiliar situations become solvable rather than scary.

## License

MIT. Copyright 0xelitesystem 2026.
