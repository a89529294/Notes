## folders in .git
### config
This is the local config file
### refs
Contains folders including `heads` & `tags`
- `refs/heads/main` contains the commit hash of the last commit on the main branch
- `refs/tags`

## Hashing Functions
Functions that match input data of *variable size* to *fixed size* output values.
*Git* uses `SHA-1` hashing function that always returns a 40 digit hexadecimal string.

## Git Database
*Git* is a key-value data store. We can insert any kind of content into a *Git* repo and *Git* will hand us back an *unique key* that we can later use to retrieve that content. These keys are *SHA-1 checksums* aka the 40 digit hexadecimal string.

## Blob
*Binary large object* are the object type Git uses to store the *content of files*, no file name or any other data.

## Trees
*Trees* are Git objects used to store the contents of a directory. Each tree contain pointers to other trees/blobs.

## Commits
*Commit* object combine a *tree* object along with info about the context that led to the current tree. Such as parent commit(s), author, commit message.
