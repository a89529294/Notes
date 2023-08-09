`find ~ -name '*keychain*'` 
- `~` start in the home directory and work through all its subdirectories
- `-name` look for patterns in the last item of a path
- use `-iname` to make it case insensitive
- slow

`locate keychain`
- fast
- updates once a week automatically
- manually update the index by `/usr/libexec/locate.updatedb`
- does partial search without asterisk
- use `locate -i keychain` for case insensitive search