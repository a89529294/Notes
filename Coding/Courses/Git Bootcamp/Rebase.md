There are two reasons to use `git rebase`:
1. as an alternative to `git merge`
2. as a cleanup tool

## alternative to git merge
1. switch to feature branch
2. `git rebase main` this moves all the commits in *feature* thats not in *main* on the tip of *main*. 
Note this generates new commits for all the moved commits. 
*main* branch is not changed.
The biggest *advantage* is that it keeps *git history linear*. 

## cleanup tool
We can rewrite, delete, reorder, rename commits using `git rebase`.
1. switch to branch you want to clean up
2. `git rebase -i HEAD~7` *HEAD~7* will be the tip you want to rebase all the later commits onto.

## When not to rebase
**Never** rebase commits that have been shared with others.

## Summary
*Rebase* on your local machine before pushing.