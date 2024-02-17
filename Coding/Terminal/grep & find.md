### `grep` is for searching file contents
```bash
grep "word" file.txt file2.txt
grep -r "word" some_dir # search through content of all files in some_dir and all its subdirectories
```

###  `find` command is for finding files and directories by name
```bash
find path -type f -name "file_name"
find path -type d -name "directory_name"
find path -name "name" # searching both files and dirs
```

### notes
- both `grep` and `find` support regex, so `*chad*` matches anything that contains `chad`. 