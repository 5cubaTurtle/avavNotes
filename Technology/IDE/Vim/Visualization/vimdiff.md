#vim 
start a diff:
`vim -d file1 file2` or `vimdiff file1 file2`

To have a decent visibility change the theme:  
`:color desert` or `:color peachpuff`

`do` -> get changes from other window into the current window
`dp` -> put the changes from current window into the other window
- `]c` -> jump to the next change
- `[c` -> jump to the previous change

- `:diffupdate` or `:diffu` -> recalculate the diff
Note that it only works if the files have been modified inside vimdiff. Otherwise, use:
- `:e` to reload the files if they have been modified outside of vimdiff.
- `:diffg RE` -> get from REMOTE
- `:diffg BA` -> get from BASE
- `:diffg LO` -> get from LOCAL

`^wx` -> swap windows

[vim-cheatsheet.md](https://gist.github.com/azadkuh/5d223d46a8c269dadfe4#vimdiff>) 