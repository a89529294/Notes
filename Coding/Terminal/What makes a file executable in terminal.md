1.  *plain text files*  containing commands in a scripting language (e.g., Bash, Python, etc.).
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

