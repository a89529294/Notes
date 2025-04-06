```bash
ls -l
-rwxrw-r-- 1 alice developers 4096 Apr  3 10:00 script.sh
```
- **Owner:** `alice` (has `rwx`)
- **Group:** `developers` (has `rw-`)
- **Others:** (has `r--`)
- _group_ is the owner's _primary group_ by default.

## common commands
- `chown user:groupName filename` use this to change a file's owner and group
- `chown user filename` use this to change a file's owner
- `chgrp groupName filename` use this to change a file's group
- `chmod <permissions> filename` change a file's permissions
	- `chmod u+rwx test-file` full access for owner
	- `chmod ugo+r-x test-file`  read for everyone, remove execute for everyone
	- `chmod o-rwx test-file` remove all access for others
	- `chmod u+rwx,g+r-x,o-rwx test-file`
	- _Or_ use numbers
	- 421 -> read, write, execute
	- `chmod 777 test-file` full access for everyone
	- `chmod 555 test-file` read, execute for everyone
	- `chmod 660 test-file` read, write for owner and group, no access for others
	- `chmod 750 test-file`, full access for owner, read and execute for group, no access for others