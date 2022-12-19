`du -sh /path/to/fodler` shows you the size of the folder
`du -sh /path/to/folder/*` shows you the sizes of each folder and files in the fodler
`find . -name "node_modules" -type d -prune -print | xargs du -chs` run this in whichever folder you store your projects. It will list out all the `node_modules` and their sizes.

`find . -name 'node_modules' -type d -prune -print -exec rm -rf '{}' \;` **delete** all found `node_modules`
