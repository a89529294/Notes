# Two ways of debugging
1. cli
2. gui

## Cli
`node inspect path_to_file` to enter cli debugging mode. Now you can type in the following commands to start your debugging session.
**Program Flow**
- `cont` or `c`: *Continue*. Continues the execution until the next breakpoint or the end of the program.
- `next` or `n`: *Step over*. Executes the next line of code.
- `step` or `s`: *Step in*. Same as above except it goes into functions instead of stepping over.
- `out` or `o`: *Out*. If the current execution context is inside the code of a function, execute the remaining code of this function and jump back to the line of code where this function was initially called.
- `restart` or `r`: *Restart*. Restarts the program and pauses the execution before the start of your code.
**Breakpoints**
- `sb()`: Add a breakpoint on the current line.
- `sb(n)`: Add a breakpoint on line `n`.
- `cb('index.js',5)`: Clear breakpoint in `index.js` line `5`.
- `breakpoints`: lists all breakpoints.
**Misc**
- `list(n)`: displays source code with `n` lines before and after current execution point.
- `exec expr`: Evaluate the expression `expr`
- `help`: show all available commands

## Gui
On the left vertical bar of vscode there is a section, `Run and Debug` or use `shift cmd d`.
Next you should see two options, *run and debug* and *javascript debug terminal*.
Either one works. 

Tips: 
- If you use *javascript debug terminal* you need to start the debugging process by `node path_to_file`. No need for the `inspect` command.
- You can add *conditional breakpoints* by right clicking on the line numbers.





