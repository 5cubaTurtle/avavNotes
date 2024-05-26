#vim 
`vi -O <file1> <file2>` - to start vi vertically-splited with 2 files in 2 windows  
  - `-o` horizontally-splitted

`:split [filename]`    - To open a file in another spilt  
`:vsplit`    - vertical split  
`:q`         -  to close a split  
`^w T`       - move the split to its own tab  
`^w r`       - swap split to right  
`^w H`       - change to vertical split  
`^w^w`       - jump to another split  
### motions  
`ctrl`+`d` Scroll down (half a screen)
`ctrl`+`u` Scroll up (half a screen)
`ctrl`+`f` Page forward
`ctrl`+`b` Page backward
`ctrl`+`y` Moves screen up one line
`ctrl`+`e` Moves screen down one line
`ctrl`+`l` Redraw screen
`ctrl`+`g` Display current line number and file information
`zt` or `z<CR>` Reposition window: cursor at top
`zz` or `z.` Reposition window: cursor in middle.
`zb` or `z-` Reposition window: cursor at bottom