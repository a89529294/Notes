*Pointers* to particular commits, they do not change unless you force them to.

## Two Types of Tags
- *lightweight tag*: a label that points to a commit.
- *annotated tag*: stores extra metadata including author name, email, tagging message.

## commands
- `git tag` lists all tags
- `git tag -l "*beta*"` lists all the tags containing `beta`
- `git checkout <tag>` checkout the commit `<tag>` is pointing to
- `git tag <new-tag-name>` creates a *lightweight tag* pointing to `HEAD`.
- `git tag -a <new-tag-name>` creates a *annotated tag* pointing to `HEAD`.
- `git tag <new-tag-name> <commit>` creates a *lightweight tag* pointing to `commit`.
- `git tag -f <tag> <new-commit>` moves `tag` to point to a different commit.
- `git tag -d <tag>` deletes `<tag>`
- `git push <remote> <tag>` pushes `<tag>` to `<remote>`
- `git push <remote> --tags` pushes all tags to `<remote>`