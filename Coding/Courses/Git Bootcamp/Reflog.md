`git reflog` is a command that displays a log of all the changes made to the Git references in your local repository, such as branch or HEAD.

Git only keep reflogs on your *local activity*. Reflogs also expire in 90 days by default.

## commands
- `git reflog show HEAD` 
- `git reflog show <branch>
- `git checkout HEAD@{10}` go to the commit where `HEAD` is at 10 moves ago.  
- `git checkout main@{2}` 

## restore deleted commits
- `git reflog show <branch>` to find the deleted commit hash
- `git reset <commit>` to restore commit history to the point `commit` is made.