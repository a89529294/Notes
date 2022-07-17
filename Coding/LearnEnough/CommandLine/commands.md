# File Permisson
1. `ls -l file_name` : gives file permisson and other metadata.
2. `stat file_name` : gives file permisson and more metadata.

# List All Users 
- `dscl . list /Users | grep -v '_'`

# Change File/Directory Owner & Group
- `chown -R owner:group <option> /path/to/fileOrDirectory` : -R means apply it recursively.

# Change File/Directory Permisson
- `chmod permissions filename` : permissions here can be _-r--r--r--_ or _444_
- `444` is the octal equivalent of -r--r--r--

# Set File/Directory Authorization and Permisson in one command
- This is a combination of the above two sections.
- `chmod u=rwx modify_it_now.exe` : _u_ is user/owner, _=_ sets permisson
- `chmod g=r+x modify_it_now.exe` : _g_ is for group
- _o_ is for others, _a_ is for all three: owner + group + others
- _=_ sets permisson, _+_ adds permisson, _-_ removes permisson




