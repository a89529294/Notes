### Creating and Switching to New Branches
- `git checkout -b <newBranch>` create and switch to *newBranch*
- `git checkout <branch2>` switch to branch2
- `git branch <newBranch>` create *newBranch*
- `git branch` lists all the branches

### Deleting Branches
- `git branch -d <branch>` deletes local branch; The branch must be fully merged in its upstream branch, or in HEAD if no upstream
- `git branch -D <branch>` deletes local branch FORCIBLY
- `git push -d <remote_name> <branch>` deletes *remote_names*'s *branch*
- Before deleting *branchA* you have to switch to a different branch first

### Resetting
- `git checkout -f` discard any changes in working and index area and switch to *HEAD* of current branch
- `git reset --hard HEAD` is equivalent to above

### Merging
- `git merge feature` make sure you are on parent branch first

### New Branches on Remote
- `git pull` if there are new branches on remote they will get pulled down automatically
- `git checkout <newBranch>` you just need to checkout the *newBranch*, notice the lack of *-b*, it means the *newBranch* is just hidden
- `git branch -a` shows all branches


