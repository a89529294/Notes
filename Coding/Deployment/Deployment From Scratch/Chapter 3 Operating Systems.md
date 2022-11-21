1. `$` => regular user; `#` => root user
2. A double dash (--) is a delimiter for options. Whatever comes after it should not be parsed by the program as another option.
3. Assigning and accessing variabls
```bash
HOSTNAME=abc
echo $HOSTNAME # abc
```
4. `$0` => current running shell script; `$?` => exit code determining if the program finished successfully or not.
```bash
uname
echo $? # 0 => success
uname -h
echo $? # 1 => error
```
5. The > sign is a stream operator that sends the output to a given file. If the file does not exist, it creates it:
```bash
echo contents > new_file.txt # creates file with string content
> new_file2.txt # creates an empty file
echo "more contents" >> new_file.txt # appends instead of overwrite
```
