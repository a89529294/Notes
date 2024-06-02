1. **Working Directory**:
    - This is where you make changes to files.
    - It reflects the current state of your project files.
2. **Index (Staging Area)**:
    - This is where you stage changes before committing them.
    - It holds a snapshot of the files that will go into the next commit.
    - It contains _all tracked files_, not just the ones with changes. This means that even unchanged files from the last commit are present in the index.
3. **Commit History**:
    - This is where committed changes are stored.
    - Each commit is a snapshot of the state of the index at the time the commit was made.

In Git everything is an object. To check the content of an object just get the object's hash and run `git cat-file -p <hash>` 
