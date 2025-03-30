```bash
type command_name # tells you wether a command is internal or external
type echo # prints echo is a shell builtin
type ls # prints ls is /bin/ls

mkdir -p China/Beijing # -p allows creation of missing intermediary directories 

file file_name # check file type, almost everything is a file, including directories
```

## bash environment variables
```bash
env # list all variables

echo $variable_name # print variable value

OFFICE=celeston # set temp local variable, for permanent variables see below
```

### For **zsh**, how to set permanent environment variables
1. **`~/.zprofile`**:
    - This file is executed for **login shells**(e.g.ssh). It's similar to `~/.profile` in Linux.
    - Use this for environment variables that should be set once when you log in.
    - Use **`~/.zprofile`** for environment variables that should be available **system-wide** (including login shells and GUI applications).
    - `export A=B` to create an **environment variable** that is available in the current shell session and all child processes 
2. **`~/.zshrc`**:
    - This file is executed for **interactive non-login shells**. It's similar to `~/.bashrc` in Linux.
    - Use this for environment variables or aliases that should be set every time you open a new terminal window.
    - - Use **`~/.zshrc`** for environment variables that should be available **only in interactive terminal sessions**.
    - `export A=B` to create an **environment variable** that is available in the current shell session and all child processes 
3. Make sure to add `export` in front of the variables in either file. Otherwise they will become local variables 