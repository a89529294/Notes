A *remote* is two things, a *name* and a *url*.
- `git remote add <name> <url>`
- `git remote rename <old> <new>`
- `git remote remove <name>`

## pushing
- `git push <remote-name> <local-branch>`
- `git push <remote-name> <local-branch>:<remote-branch>`
- `git push -u origin master` sets the upstream of the *local* master branch so that it tracks the *origin* repo's master branch. Next time you are on master branch you can just `git push`.
- `git branch -vv` to check *upstream* branches.
- `git push -u origin master:newMaster` sets the upstream of the *local master* branch so that it tracks the *origin repo's newMaster* branch.

## remote tracking branch
A *reference* to the state of a branch on the remote. This branch gets set up when you run `git push -u <remote> <local-branch>`. Also happens when you `git clone` a repo with a default branch.

"At the time you last communicated with this remote repo, here is where x branch was pointing"
- `origin/master` references the state of the *master* branch on the _origin_ repo. 
- `upstream/logoRedesign` references the state of the *logoRedesign* branch on the *upstream* repo.

## after git clone
Right after `git clone <remote-url>` you have a local default branch connected to the remote default branch via *remote tracking branch*. Usually this means local `main` is connected to repo's `main` via `origin/main`.
Now run `git branch -r` you will see you actually have *all the branches on the remote locally*, but they are under remote tracking branches, `origin/branchA`, `origin/branchB`. 
In order to work with them locally, run `git sw branchA`.

## fetching
"go and get the latest information from a remote, but don't mess up my local working directory."
- `git fetch <remote>` updates all remote tracking branches
- `git fetch <remote> <remote-branch>` updates specified remote tracking branch

## pulling
- `git pull` updates all remote tracking branches; merges current local branch with its remote tracking branch; repo defaults to `origin`.
- `git pull <remote> <remote-branch>`: fetch and merge `remote-branch` into `current-branch`.