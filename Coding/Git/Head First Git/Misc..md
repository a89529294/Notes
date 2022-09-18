## Tags
Named references to commits just like *branches* BUT they never move.

`git tag v1.0.0` by default this labels the `HEAD` as `v1.0.0`
`git tag v2.0.0 049896f` labels the commit `049896f` as `v2.0.0`
`git tag -l` lists all tags

## Git Cherry-pick
Let's say you are working on `feat-a` which has multiple commits already. One of the contains a bug fix. You are not ready to merge the whole branch into `main`. What can you do?
`git switch main` then `git cherry-pick commit_id_of_bug_fix`. Git will create a copy of the commit on top of the `main` branch.

\*\* This new commit of the `main` branch will contain the same set of changes as the `bug_fix` branch, but they will have different commit ids.

## Stashes (pseudo commits)
Two differences from commits
1. It saves the changes in *working* and *index*
2. Stashes are local and do not add to the commit history

`git stash` then `git switch feat-a` then `git stash pop --index` 
`git stash` equivalent to `git stash push` Save your local modifications to a new stash entry and roll them back to HEAD (in the working tree and in the index).
`git stash pop` Remove a single stashed state from the stash list and apply it on top of the current working tree state
`git stash pop --index` on top of the above, also tries to reinstate the changes in index

## Reflog
`git reflog` records the commit id everytime `HEAD` moves

## Git Rebase


