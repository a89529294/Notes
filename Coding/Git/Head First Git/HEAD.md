`HEAD` is another refernce to a commit just like `branch_name`. The difference is `HEAD` always points to the commit you are on.

Usually `HEAD` points towards the *latest commit* on a branch. It can also point to an *arbitrary* commit, it that case it is called a *detached HEAD*.

## Referencing Commits with HEAD
`HEAD~1` refers to the parent of `HEAD`. `HEAD~2` refers to the grandparent of `HEAD`.

`git diff HEAD~1 HEAD` compares the previous commit to the latest commit.

What about commits with *two* parents? e.g. a merged commit. 
- The integration branch(the branch you are on when you run `git merge ...`) latest commit is `HEAD^1`; the integrated branch latest commit is `HEAD^2`.
- If you use `HEAD~1` it will refer to `HEAD^1` in this case. Basically `~n` will refer to the integration branch's commits.
	

You can combine `^` and `~` like so `HEAD^1~1` which refers to the integration branch latest commit(before merge)'s parent. 