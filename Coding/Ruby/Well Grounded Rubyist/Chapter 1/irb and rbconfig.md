`irb -r rbconfig` load module rbconfig
`irb -I '.'` add current dir to $LOAD_PATH
`ruby -e 'puts 1 + 1'` tells Ruby to evaluate string 

Once *rbconfig* is loaded you can access `RbConfig::CONFIG`. A hash containg info about ruby installation.
- RbConfig::CONFIG['rubylibdir'] shows where Ruby *standard libraries* are installed
- RbConfig::CONFIG['bindir'] shows executables like `ruby`, `irb`, `rails` 
