#git 
Add file contents to the index

`git add <path>`: Stage a specific directory or file
- `--interactive, -i` enter interactive mode
- `--patch, -p`: Interactively stage hunks of changes
- `-A`: stages all files, including new, modified, and deleted files, including files in the current directory _and_ in higher directories that still belong to the same git repository
-   `.`: adds the entire directory recursively, including files whose names begin with a dot. But not higher directories.
-   `-u`: Update the index just where it already has an entry matching \<pathspec\>. This removes as well as modifies index entries to match the working tree, but adds no new files.
- `-N`, `--intent-to-add`: Record only the fact that the path will be added later. An entry for the path is placed in the index with no content.

| The Flag     | New files | Modified files | Deleted files | Files with names beginning with a dot | Current directory | Higher directories |
| ------------ | --------- | -------------- | ------------- | ------------------------------------- | ----------------- | ------------------ |
| `git add -A` | Yes       | Yes            | Yes           | Yes                                   | Yes               | Yes                |
| `git add .`  | Yes       | Yes            | Yes           | Yes                                   | Yes               | No                 |
| `git add -u` | No        | Yes            | Yes           | Yes                                   | Yes               | Yes                |

Undo staging use either [[restore]] or [[reset]] commands:
`git restore --staged <file>` or `git reset HEAD` (aka `git reset --mixed HEAD`).

exclude some files during **add**:
```git
git add --all -- ':!path/to/file1.txt' ':!path/to/file2.txt' ':!path/to/folder1/*'
```