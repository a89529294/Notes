To ignore a directory suffix the name with `/` like so `my_dir/`

To *untrack* a file that is already staged or commited run `git rm --cached file_name`, make sure the file name is added in `.gitignore` then next time you run `git add -A` the file will not be included.

To *untrack* everything `git rm --cached -r .` 