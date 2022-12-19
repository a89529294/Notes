###### Minimum Viable Vim
- `vim`: type this in iterm to open vim
- `esc :q! return`: to exit vim
- Two modes in vim, *insertion* & *normal* mode
- Vim starts in *normal* mode, switch to *insertion* mode by pressing `i`; switch back by pressing `esc`
- In *normal* mode, `0` to move cursor to start of line; `$` to move cursor to end of line
- In *normal* mode, press `u` to undo previous edit
- In *normal* mode, move cursor to a character then press `x` to cut it. You can also cut an entire line by pressing `dd`. `p` to paste what you just cut
- `:w` to write; `:wq` to write then quit
- Moving around a file is actually the same as *less*. 
	- `^f` to move forward a page; `^b` to move back a page
	- `/<string>` to look for *string* case sensitive; `n` to go to next occurence; `N` to go back to previous occurence
	- `1G` to go to first line; `G` go to last line; `18G` go to line 18
 