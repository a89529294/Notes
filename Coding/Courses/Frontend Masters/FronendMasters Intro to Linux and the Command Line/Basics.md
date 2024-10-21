- Bash is actually a programming language
- the terminal is a REPL, executing your bash code one line at a time

## flags
- you can pass in the same flag multiple times, `ls --ignore=x --ignore=y`
- some programs do not care about where you put the flags, some do. As a rule of thumb, put it right after the command, `ls -al my_dir`.

## bash history
- up and down arrows
- `ctrl + r` lets you search through command history, `ctrl + r` again displays one command at a time.
	- `ctrl + r` then type `ls` then `ctrl + r` again, it will show you all the commands that start with `ls` one at a time
- 