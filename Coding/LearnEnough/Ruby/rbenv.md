- `ls ~/.rbenv/versions/` to *list* all installed ruby versions
- `rbenv install -l` to *list* all latest stable versions
- `rbenv install 3.1.2` to *install* a specific version
- `rbenv rehash` Installs shims for all Ruby executables known to rbenv (i.e., `~/.rbenv/versions/*/bin/*`). Run this command *after you install a new version of Ruby*, or install a gem that provides commands.
- `rm -rf ~/.rbenv/versions/3.1.2` to *uninstall* a specific version
- `cat ~/.rbenv/version` or `rbenv global` outputs the *global* ruby veriosn
- `rbenv global` *shows* the *global* ruby version
- `rbenv global 3.1.2` *changes* the *global* ruby version
- `rbenv local` *shows* the *local* directory's ruby version
- `rbenv local 2.7.4` *changes* the *local* directory's ruby version
- 

### Misc.
- `echo "gem: --no-document" >> ~/.gemrc` to skip installing gem documentation
