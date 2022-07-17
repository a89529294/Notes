### Autocomplete
- In *VSCode* `ctrl space` gives you a list of suggestions

### Making a Shell Script
- The shell script we made is called `ekill` which is located in `~/bin/ekill`
- In order to make it work we need to make sure of two things
	1. The directory(`~/bin`) where we store the script is on the `$PATH`, check using `echo $PATH`. If it is not go to `~/.zshrc` then add `export PATH="$HOME/bin:$PATH"`
	2. The script it self is executable, check by `ls -l ~/bin/ekill`. If it is not issue `chmod +x ~/bin/ekill`
	3. Finally check if `ekill` is ready to use `which ekill`

### Editing Projects
- `cmd p` to open fuzzy search for files
- `cmd f` find in a single file
- `option cmd f` find and replace in a single file
- `shift cmd f` global find in project
- `cmd b` to toggle explorer panel
	- then `shift cmd f` to switch to global find, `shift cmd e` to go back to explorer

### Switching Between Editor Windows
- `shift cmd tilde`

### Closing Tabs & Windows
- `cmd w` to close current tab
- `shift cmd w` to close current window

### Regex
- Good [resource](https://regex101.com) for regex building
- use () to denote groups, $1, $2 to refer to them. 

