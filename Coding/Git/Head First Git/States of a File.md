Three areas of git
	1. Working directory
	2. Staging/index
	3. Object database

Any file in your working directory is either *tracked* or *untracked*.
Any *tracked* file can be either **staged**, **unmodified**, or **modified**.

Git adds a *copy* of a file when you move a file from working to index or index to object db.

A file is *unmodified* if all exisiting copies are the same.
- If the file has never been commited, it means the copies of the file are the same in *working* and *index*
- If the file has been commited before, it means the copies of the file are the same in *working*, *index*, and *object db*

A file is modified if the copy in *working* is different from the one in *index*, or if the copy in *index* is different from the one in *object db*.
