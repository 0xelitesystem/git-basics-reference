# Rebase vs merge

Merge and rebase both integrate changes from one branch into another, but they do it differently: merge creates a new commit that joins two histories and preserves them as they happened, while rebase moves your commits to start from the tip of another branch, rewriting them into a straight line. Merge keeps history honest; rebase keeps it tidy.

## What merge does

Merging takes two divergent branches and combines them with a merge commit that has both branch tips as parents. The original commits stay exactly where they were, and the merge commit records that the two lines came together. The result is a history that shows the real shape of the work, including where branches split and rejoined. Nothing is rewritten, so merging is always safe to do on shared branches.

## What rebase does

Rebasing takes the commits unique to your branch and replays them one by one on top of another branch's latest commit, as if you had started your work from there. This produces a linear history with no merge commit. The key fact is that rebase creates new commits with new hashes, even though the changes are the same. Your old commits are replaced by the rewritten copies, which is why rebase is described as rewriting history.

## The golden rule

Do not rebase commits that other people have already pulled. Because rebase rewrites commits into new ones, rebasing shared history makes your copy disagree with everyone else's, causing confusing duplicate commits and broken pulls. The safe rule: rebase only your own local commits that have not been pushed and shared. On commits others have, use merge. This single rule prevents most rebase disasters.

## Choosing between them

Use merge when you want a faithful record of how work actually happened, or whenever the branch is shared. Use rebase to clean up your own local commits before sharing them, for example to update your feature branch onto the latest `main` so it applies cleanly and reads as a straight line. Many teams rebase local work to stay current, then merge the finished branch in. Both are valid; the choice is about honest history versus tidy history, constrained by the golden rule.
