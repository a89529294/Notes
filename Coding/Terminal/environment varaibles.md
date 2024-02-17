## variables
```bash
name="Albert"
echo $name
```
This only lives in the current shell, sub processes like scripts have no access to _variables_ defined this way.

## environment variables
```bash
export name="Albert"
echo $name
```
Sub processes like scripts have access to this _environment variable_. `PATH` is also set this way in `~/.zshrc`. 
Every time you open a terminal, `~/.zshrc` runs and environment variables like `PATH` is set.

```bash
unset name
```
This unsets the variable name.
## PATH
The `PATH` variable is a list of directories that your shell will look into when you try to run a command. If you type `ls`, your shell will look in each directory listed in your `PATH` variable for an executable called `ls`. If it finds one, it will just run it. If it doesn't, it will give you an error like: "command not found".
