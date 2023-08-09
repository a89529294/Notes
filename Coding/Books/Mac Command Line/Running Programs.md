You can run a program in any of three ways, depending on where the program is located, your current position in the directory structure, and what’s in your PATH
- _By relative or absolute path_: You can always run a program by entering its complete path, such as `/usr/bin/less`
- _In the current directory_: You must precede the name of the program with `./`. For example, to run a program named counter in the current directory, enter `./counter`.
- _In your PATH_: Simply enter your program's name, such as `less`.

## Find out what processes are currently running
**Dynamic List**
`top`: by default order by cpu usage
`top -o rsize`: order by memory usage
`top -o pid`: roughly in order of how recently they were launched 
`top -n 10`: lists only 10
**Static List**
`ps -ax`
`ps -ax | grep /Applications`: lists all processes running from inside /Applications
