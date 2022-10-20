- `open .`: opens the current directory in file finder
- `open foo.pdf`: opens the pdf using default program for pdf
- `open xxx`: opens xxx using its default program
- `mkdir -p ~/foo/bar`: option p creates intermediate directories if needed
- `ls -dl my_dir`: lists info about directory instead of showing its content
- `cd` & `cd ~` are equivalent
- `find . -name '*.txt'`: find recursively file with name matching \*.txt
- `find ~/Desktop/code -type d -name '*skeleton*'` find directory with *skeleton* in its name under the path *~/Desktop/code* 
- `mdfind kind:folder 'skeleton' -onlyin some_path` this will look for directories with *skeleton* in its metadata
- `cd -`: return to the previous directory

###### Combining Commands
- `./configure ; make ; make install`: runs three commands; all commands will run even if some of them fail
- `./configure && make && make install`: runs the next command if and only if the previous one succeeds

###### Renaming, Copying, Deleting Directories
- `mv foo bar`: rename foo/ to bar/
- `cp -r foo/ bar`: copy foo/ *content* to bar/
- `cp -r foo bar`: copy foo/ itself to bar/
- `rm -rf foo`: removes foo/ 

- `grep -ri sesquipedalian text_files`: look for the string *sesquipedalian* case insensitively in files in text_files/ and its sub directories

