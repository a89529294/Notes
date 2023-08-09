1. `nano my_script.sh`
2. add `#! /bin/zsh` as the first line
3. add the following as an example
```zsh
echo "Hello!, the current date and time is:"
date
echo "And the current directory is:"
pwd
```
4. `ctrl O`, then press `enter` to save file.
5. `chmod u+x my_script.sh` to make it executable
6. `./my_script.sh` to run it.