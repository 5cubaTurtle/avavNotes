#git 

Restore working tree files

`restore` can be used to revert work in the working copy or the index, or both.

The command can also be used to restore the content in the index with `--staged`, or restore both the working tree and the index with `--staged` `--worktree`.

`--source` could be used to specify a commit as the restore source:

| |default source|`--source`|flag to set destination|
|---|----|--------|----|
|working-copy|index| as specified|[`--worktree`] (default)|
|index|HEAD| as specified|`--staged`|
|*both*| -- | as specified|`--staged` `--worktree`|

restore file from index to workspace:   `git restore <file>`
restore a specific historic revision of a file:
```shell
git restore --source=7173808e index.html
git restore --source=master~2 index.html
```
restore a file as it was before some specific old commit:
`git restore --source=7173808e~1 index.html`
- `7173808e~1`  means 1 commit before the `7173808e` commit

restore all files in the current directory (in working-copy):   `git restore .`, this cannot be undone if the files are not added to index

restore a file in the index to match the version in HEAD (this is the same as using git-[[reset]](1)):  `git restore --staged hello.c`  (if the change was added to index from the working-tree, it will still be present in the working tree). Equal to `git reset HEAD <file>`.

or you can restore both the index and the working tree (this the same as using git-[[checkout]](1)):   `git restore --source=HEAD --staged --worktree hello.c`

restore interactively. Allows selection of specific code section to restore: `git restore -p some/file`
