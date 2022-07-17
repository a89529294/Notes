### Setup
- `~/.gitconfig` is your global git config file
- `git --version` to check git version
- `git help` to see different git commands
- `git help <gitCommand>` to see how to use a specific git command

### Initializing a Git Repo
- `git init` in the directory you wish to track
- `ls -a` too see a hidden *.git* file created

### First Commit
- `git status` to check status of files in the repo
- `git add .` or `git add -A` to add all files to the index
- `git commit -m <msg>` to commit to local repository
	- *msg* should be in **present tense** using **imperative mood**
- `git log` to see commit history

### Diffing
- `git diff` shows changes between working tree and index(staging)
- `git diff --staged` compares staging to repository (last commit)
- `git diff HEAD` compares working to repositoy
- `git diff branchA branchB` compares tip of *branchA* and tip of *branchB*
- `git diff branchB` compares tip of *branchB* to tip of current branch

### Misc.
- `git add -A` does two things 
	- for tracked files it stages them
	- for untracked files it tracks then stages them
- `git commit -am <msg>` to stage tracked files and commit them in one command, untracked files will be ignored
- `git commit --amend` to amend last commit's message
- Four areas
	1. working tree
	2. staging/index
	3. local repository
	4. remote repository
- Go from *working* to *index* by `git add`; go from *index* to *local repo* by `git commit`; go from *local repo* to *remote repo* by `git push`

