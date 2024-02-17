- `du -a path_to_dir | sort -n -r | head -n 20` list largest 20 files

### info on files and directories
```bash
ls -l "file_name"
ls -l "directory_name" # show info on files in dir
ls -ld "directory_name" # show info on dir itself
ls -l # show info on all files and directories in current dir
```

### view file content - simple 
```bash
cat file.txt
head -n 10 file.txt
tail -n 10 file.txt
```

### view file content - advanced
```bash
less -N file.txt # -N to display line number
# up and down arrow to move one line at a time
# space to move down one page, b to go back one page
# q to quit
```

### copy file and directories
```bash
cp file.txt folder/ # copy file.txt to folder
cp -R my_dir new_dir # copy a dir and all its content
```


