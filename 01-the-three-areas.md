# The three areas

Git moves your work through three areas: the working directory where you edit files, the staging area (also called the index) where you assemble the changes for your next commit, and the repository where commits are stored. Understanding these three areas explains why staging and committing are separate steps and what every basic command is actually doing.

## The working directory

The working directory is the folder of actual files you see and edit. It holds the current state of your project as it exists on disk. When you change a file, that change lives only in the working directory until you do something with it. Git calls a file with uncommitted edits "modified." The working directory is the only place you directly touch files; everything else is Git's internal bookkeeping about them.

## The staging area

The staging area is where you assemble exactly what your next commit will contain. When you run `git add` on a file, you copy its current state into the staging area, marking it to be included in the next snapshot. This extra step lets you commit some changes and not others, so a single commit can be a clean, logical unit even if your working directory has unrelated edits in progress. A staged file is one whose changes are ready to be recorded.

## The repository

The repository is the permanent store of commits, kept in the hidden `.git` folder. When you run `git commit`, Git takes everything in the staging area and records it as a new snapshot with a message, an author, and a link to the previous commit. Commits are immutable: once made, a commit's content does not change. This is what makes Git history reliable. The repository is your project's full recorded history, not just its current files.

## How a change flows

A typical change flows through all three areas in order. You edit a file (working directory), you stage it with `git add` (staging area), and you record it with `git commit` (repository). The same file can have different versions in each area at once: edited on disk, an earlier version staged, and an earlier version still committed. Reading `git status` is mostly about seeing where each file sits across these three areas.
