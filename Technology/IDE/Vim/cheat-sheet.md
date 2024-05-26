#vim 
![[Vim-cheatsheet.png]]
### [vi cheat sheet.pdf](http://www.atmos.albany.edu/daes/atmclasses/atm350/vi_cheat_sheet.pdf)
[vim-cheatsheet.md](https://gist.github.com/azadkuh/5d223d46a8c269dadfe4#vimdiff>),  [another one](https://vim.rtorr.com/), and [another](https://devhints.io/vimscript) 

Invoking vi: `vi filename`
#### Input commands
`r` Replace single character with: `rc` will replace the character under the cursor with `c`.
`R` Replace until stopped, i.e. enter replace mode (similar to [[insert-mode]]).
`s` Substitute char, or use `S` to substitute the entire line.
`.` Repeat last change
`x` Delete a character

#### Undo commands
`u` Undo last change
`U` Undo all changes on line
`ctrl`+`r`  redo last undo

#### Regular expressions (search strings)
`^` Matches beginning of line
`$` Matches end of line
`.` Matches any single character
`*` Matches any previous character
`.*` Matches any character
