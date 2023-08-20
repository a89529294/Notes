There are two ways of _finding files_ by _name_, __find__ & __locate__.
If you want to search by _content_, use __grep__.

## `find ~ -name '*keychain*'` 
- `~` start in the home directory and work through all its subdirectories
- `-name` look for patterns in the last item of a path
- use `-iname` to make it case insensitive
- slow

## `locate keychain`
- fast
- updates once a week automatically
- manually update the index by `/usr/libexec/locate.updatedb`
- does partial search without asterisk
- use `locate -i keychain` for case insensitive search

## Grep
`grep -R "Apple" .` searches recursively within contents of all files, starting from current directory.
`grep "Apple" *` searches contents of all files in current directory.

You can also use _regex_ instead of plain strings.
### regex basics
- Any character `.`
- One of more times `+`
- Anything in a particular set of characters `[]`. For example, `[abcde]` for any of the letters `a,b,c,d,e`; or `[1-5]` for any digit 1 through 5.
- Anything NOT in a particular set `[^]`.
- Start of line `^`
- End of line `$`

### examples
- `grep -RIE "Apple\s[A-Za-z]+$" .` `-I` means ignore binary files, `-E` means treat this as a _regex_. 