_Executable files_ are just programs that you can run on your computer.
Files with a `.sh` extension are [shell scripts](https://en.wikipedia.org/wiki/Shell_script). They're just text files that contain shell commands. You can run a file in your shell by just typing its file path.

### What makes a file executable
1.  *plain text files*  containing commands in a scripting language (e.g., Bash, Python, etc.). You need to add a shebang line as the first line, see next section.
2. *executable binaries*

### plain text files
For *bash file* you need 
```bash
#!/bin/bash
```
as the first line

for *python file* you need
```zsh
#!/Users/albert/.pyenv/shims/python
```
as the first line

Then you can just run `./myScript.py` or `./myShell.sh`

### Note
Make sure the files execute permission is set by `chmod +x file.sh` 

