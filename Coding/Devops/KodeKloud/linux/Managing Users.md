- `useradd bob`
	- `grep -i bob /etc/passwd` to verify
	- `passwd bob` to set password
	- both `useradd` and `passwd` need to be ran as root
- `passwd`
	- `passwd bob` can be used to set password for `bob`
	- `passwd` can be used to set password for current user
- `userdel bob`
	- delete user bob
- `groupadd -g 1011 developer`
- `groupdel developer` 