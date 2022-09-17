A *detached HEAD* is simply the case when you are on a commit that is not the tip of a branch.

You can still make commits when you are on a *detached HEAD* just like you would on a normal *HEAD*. 

The difference is normally when you commit, git automatically moves the branch to the newest commit. For example, if you are on *feat-a* branch and you make a new commit. *feat-a* will move automatically to the new commit.

On a *detached HEAD*, you are not on a branch (remember branch refers to tip of a branch), so when you commit, you move the *HEAD* but there is no branch to move. Once you switch back another commit. *The commit you just made will be gone since no branch is referencing it.*

In order to solve this, once you enter a *detached HEAD*, and if you know you want to make commits, simply `git switch -c new_branch` to create and switch to a new branch. Now you are on a branch. Once you create a new commit, git will move the branch forward. 