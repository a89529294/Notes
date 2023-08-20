## Pipe |
The pipe operator, sends the output of a command to another program.
_syntax_: `program | other-program`

### Examples
- `ls /Library/Preferences | tail -n 15` lists last 15 items
- `pwd | pbcopy` copies current directory path

### misc
- If a command can accept a file as an argument, it can probably be used on the right side of a pipe.

## Output Redirect > & Output Append >>
Whereas the pipe sends the output of a program to another program, the redirect output (>) operator sends the output of a program to a file (without displaying it on screen).
_>_ replaces the content of target file, _>>_ adds to the content of target file.
### examples
- `ls /Library/Preferences > ~/Desktop/prefs.txt`

## Input Redirection <
_>_ sends the output of a program to a file. _<_ redirect the input of LHS to RHS.
### examples
- `pbcopy < ~/Desktop/prefs.txt`
- 




