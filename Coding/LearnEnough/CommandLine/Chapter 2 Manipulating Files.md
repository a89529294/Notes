- `cat fileName`: reads the file and returns the string to stdout
- `cat fileName > my_new_file.txt`: redirects the output of cat to the new file
- `cat fileName >> my_new_file.txt`: appends the output of cat to the new file
- `echo "hello, world" > other_file.txt`: redirect and append can be used with other commands as well
- `cat file_1 file2`: cat can take multiple files and concatenate them

- `ls`: list non hidden files and directories
- `ls -lh`: list non hidden files and directories in long form and display size in kb, mb if nec.
- `ls -la`: list all files and directories in long form
- `ls -t`: list non hidden files and directories from most recent at top
- `ls -rt`: list non hidden files and directories from most dated at top
- `ls *a*`: list non hidden f & d using wildcards, will match cat.txt zzadd/, etc
- `ls -d *a*`: same as above but don't show matching directories' contents 

##### Switching Shells
- check shell use: `echo $SHELL`
- switch to z shell: `chsh -s /bin/zsh`
- switch to bash: `chsh -s /bin/bash`

- `mv foo.txt bar.txt`: rename foo.txt to bar.txt
- `cp foo.txt baz.txt`: copy foo.txt to baz.txt
- `rm foo.txt bar.txt`: remove foo.txt & bar.txt
- `rm -f foo.txt` : force remove foo.txt, no need for confirmation

