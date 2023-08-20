## Introduction
Permissions consist of _three possible activities_ (reading, writing, and executing), performed by any of _three types of user_ (the file’s owner, the file’s group, and everyone else). 
Three types of permission multiplied by three types of user equals _nine items_, each of which can be specified individually for any file or folder.

## Read, Write, Execute
Someone with permission to _read_ a file can open it and see what’s inside it. Someone with _write_ permission can modify an item or delete it. _Execute_ permission, for a file, means it can be run (that is, it can behave as a program or script); for a directory, execute permission means someone can list its contents.

## User, Group, Others
- _user_: owner of a file or directory.
- _group_: each file and directory also has an associated group—one or more users for whom a set of permissions can be specified.
- _others_: every user who is neither the owner nor in the file's group is lumped in

## Reading the output of ls -l
`drwx------@   6 albert  staff       192 Oct 19  2022 Applications`
- `d` means directory
- chars 1-3 represent the permissions for user
- chars 4-6 represent the permission for group
- chars 7-9 represent the permission for everyone else
- the number `6` means there is 6 items in `Applications`
- `albert` is the user/owner
- `staff` is the group
`-rw-r--r--@   1 albert  staff      3281 Jul  6  2022 README.md`
- `-` the first dash means it is a file

## Modifying an Item's Permissions
`chmod u+x file1`: reads as _add execute_ for _user_ of `file1`
`chmod ugo+x file1`: _add execute_ for _user_,_group_,and _others_ of `file1`
`chmod u-x,o+r file1` _remove execute_ for _user_, _add read_ for _others_ of `file1`
`chmod go-rwx file1`: remove all permissions for group and others of `file1`

### absolute mode - changing everyone's permissions at once
`chmod 755 file1`: user can rwx, group and others can rx.  
- 4: read
- 2: write
- 1: execute

## Changing an Item's Owner or Group
`chown bob file1` change the _owner_ of file1 to bob
`chown bob:accounting file1` change the _owner_ to bob, and _group_ to accounting
`chown :accounting file1` change the _group_ only
