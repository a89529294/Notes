## touch
`touch file1`
Serves two purposes:
- When supplied with the name of a nonexistent file, creates an empty file.
- When supplied with the name of a existing file/folder, updates its modification date time to the current date time.

## mkdir
`mkdir folder1`
- if you want to create a hierarchy of directories while some of them don't already exist, use `mkdir -p folder1/folder2/folder3`

## cp
`cp file1 DestinationFolder`
- copies file1 into DestinationFolder
- if DestinationFolder does not exist, it will assume Destination folder to be new file name.
`cp -r Folder NewFolder`
- add -r recursive flag to copy folders
- pay attention to `Folder` or `Folder/` `/` means you want to copy the content of `Folder` into `NewFolder`. 

## mv
`mv fileOrFolder newName`
- renames the file/folder
`mv fileOrFolder DestinationFolder`
- moves file/folder to new folder
`mv *.jpg Pictures`
- moves all the files from the current directory ending in .jpg into the Pictures directory.
