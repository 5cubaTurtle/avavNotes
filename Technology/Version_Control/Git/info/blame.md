#git
Show what revision and author last modified each line of a file.

`git blame filename.txt`
- `-w` ignore whitespace changes
- `-L 100,150` only display lines 100 to 150. `100,+5` will display lines 100 to 104.

Annotate file at revision specific revision (*d9dba0*): `git blame d9dba0 filename.txt`
Add a global alias for "praise": `git config --global alias.praise git blame`
