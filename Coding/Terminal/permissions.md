The _permissions_ of an individual file or directory are visually represented as a 10-character string: `drwxrwxrwx`.
- The first one just tells you whether you're looking at a file or a directory:
	- `-` means file
	- `d` means directory
- The next 9 characters are broken up into 3 sets of `rwx` and represent the permissions themselves for the "owner", "group", and "others".
	- `rwx`: All permissions
	- `rw-`: Read and write, but not execute
	- `r-x`: Read and execute, but not write

## changing permissions
The [chmod command](https://www.ibm.com/docs/fr/aix/7.1?topic=c-chmod-command) lets you change the permissions of a file or directory. It's short for "change mode"

```bash
chmod -R u=rwx,g=,o= "dir_name"
# -R means recursive, u is user, g is group, o is others

chmod +x "file_name" # sets file to be executable for user, group and others

chmod -x "file_name" # sets file to be un-executable for user, group and others
```

## changing owner
`chmod` allows you to change the permissions of any file or directory that you own.

`chown` command allows you to change the owner of a file or directory, and it requires root privileges.

```bash
sudo chown -R root contacts
# root is the new user
# contacts is the directory
```




