## find (locating files/directories)
primarily used for searching _files and directories_ based on their attributes (such as _name_, _size_, _modification time_, etc.)

### syntax
`find /bar -type f -name foo.txt`
`find <dir> <option> <file/folder>`
"Search in the _bar_ directory for a file named foo.txt"
`-type d` for directory

## grep (search within files)
search file _contents_

### syntax
`grep -i "xxx" /var/www/foo.txt`
"look for xxx within foo.txt case insensitively"
`grep -i "apple" *.log`
"look for apple in all files that end in .log"