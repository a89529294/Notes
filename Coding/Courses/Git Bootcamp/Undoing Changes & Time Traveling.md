## detached head
the *HEAD* in Git points to the *current commit your working directory is based on*, and it can be either pointing to a *branch*(latest commit on a series of commits) or a specific *commit* in a *detached HEAD state*.

`git checkout <commit-hash>` to enter *detached HEAD state*, now you have a couple of options:
1. Stay in detached HEAD to examine the contents of the old commit.
2. Leave and go back to wherevr you are before, `git sw <branch>`.
3. Create a new branch based on the commit you are on, `git sw -c <new-branch>`.

## discarding changes with checkout
`git checkout HEAD <file1> <file2>`: git discards changes in working directory to match the versions of `file1` & `file2` in HEAD.

## git restore 
*Restore files back to the state in HEAD*, unless otherwise specified.
`git restore <file1> <file2>`: does the same thing as `git checkout HEAD <file1> <file2>`.
`git restore --source HEAD~2 <file>`: restore content of `file` to match file in `HEAD~2`.

## git restore --staged
*Unstage a file*, i.e. remove a file from *staging area*. 
`git restore --staged <file>`

## git reset
*removes the commits, but not the changes in your working directory*.
`git reset <commit>` removes all the commits after `<commit>`. In other words, your commit history becomes the same as when you added `commit`. 

## git reset --hard
*removes the commits, as well as all the changes in working directory*.

## git revert
*revert* & *reset* are similar in that they both *undo* commits, but in different ways.
- `git reset` removes the commits
- `git revert` creates a new commit that undos the changes from a commit or multiple commits. 
`git revert <commit1> <commit2>`

## misc
- `git checkout HEAD~1` checkout parent of HEAD
- `git switch -` moves HEAD to the previous commit, can use this to toggle between commits.
