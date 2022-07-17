- `which <programName>`: locate a program, such as *which curl*, *which git*
- `!!`: repeat the last command
- `!c`: repeat the last command that starts with c
- `^R`: search though previous commands 

- `head file.txt`: shows first 10 lines of file
- `head -n 20 file.txt`: shows first 20 lines of file
- `tail -n 20 file.txt`: shows last 20 lines of file
- `wc file.txt`: shows how many lines, words, bytes is in file.txt
- `head file.txt | wc`: pipes output of LHS as input of RHS; shows lines, words, bytes of output of LHS

###### Curl
- `curl -OL <urlAddress>`: downloads the resource at *urlAddress* to current directory. `-O` saves the file with the remote name otherwise it gets dumped to stdout. `-L` follows redirects
- `curl -o <path/fileName> <urlAddress>`: downloads the resource at *urlAddress* using the name *fileName*
- `curl -I urlAddress`: fetch the headers only
- `curl -o path/name --create-dirs https://.....` will create necessary directories if needed

###### LESS: A better way of displaying file contents
- `less file.txt`: display file content in stdout
- `arrouw up & down`: move file up and down by one line.
- `spacebar` or `^f` move file down one page 
- `^b` move file up one page
- `G` move to end of file; note capital G, so keypress is `shift g`
- `1G` move to start of file; keypress `1 shift g`
- `17G` move to line 17 of file
- `/<string>` search for string; `n` to move to next occurance; `N` to move to previous occurance
- `q` to quit less
- `man` pages uses less

##### GREP
- `grep rose sonnets.txt`: displays all lines containing substring rose, case sensitive.
- `grep -v rose sonnets.txt`: displays all lines NOT containing substring rose. case sensitive.
- `grep -i rose sonnets.txt`: case insensitive search
- `ps aux | grep server`: get all prcoessess pipe it to grep to display all processess containing the word server, the first number is the pid
- `kill -15 pid`: to kill process with pid
- `pkill -15 -f spring`: kill all processess containing the name spring