A *branch* in Git *always points to the latest commit* on that branch.

When you *create a new branch*, Git creates a *new pointer that initially points to the same commit as the branch* you created it from (usually the latest commit on the main development branch). As you make new commits on the new branch, Git updates the branch pointer to point to the most recent commit on that branch.

the *HEAD* in Git points to the *current commit your working directory is based on*, and it can be either pointing to a *branch*(latest commit on a series of commits) or a specific *commit* in a detached HEAD state.

## deleting branches
`git branch -d <branch-name>`
`git branch -D <branch-name>`
Deleting a branch *only removes the pointer to the commit at the tip* of the branch; the commits themselves are not deleted. *If the commits in the deleted branch are not also part of other branches or tags, they may become unreachable and eventually be removed* by Git's garbage collection process. However, if the commits are part of other branches or tags, they will continue to be accessible.

## switching branches
`git switch -c <new-branch-name>`
`git switch <branch-name>`
*switch* moves the `HEAD` pointer to point to the specified branch

## merging
We always merge to w.e branch *HEAD* is pointing to.
Say we have two branches `A` and `B`, if we want to merge `B` into `A`:
1. `git sw A`
2. `git merge B`

## commands
- `git branch` lists local branches
- `git branch -a` lists all branches
- `git branch -r` lists remote branches
- `git branch -vv` lists local bracnhes and their upstreams

## misc
- the term *"branch"* in Git can refer to a *series of commits* that represent a separate line of development, or it can refer to the *latest commit on a branch*, which represents the current state of the branch.
- When you create a new file in branch A but haven't committed the changes, the new file is still present in the working directory of branch A. When you switch to branch B, the working directory is updated to reflect the contents of branch B, but *any uncommitted changes in new files in the working directory will still be present*. It is a good idea to commit/stash any changes before switching branches.