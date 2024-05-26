#vim 
`:h insert-mode`
### Entering insert mode
`a` Append after cursor. `A`  append at the end of line.
`i` Insert before cursor. `I` insert in the beginning of the line.
`o` Open line below. `O` Open line above
`cw` Change word
`cc` or `S` Change line - blanks line
`c$` Change to end of line
`R` Replace - type-over
`s` Substitute - 1 char with string
`S` Substitute - Rest of line with text

### cursor motion
`ctrl`+`h` Delete backward one character
`ctrl`+`w` Delete backward one word
`ctrl`+`u`Delete backward to beginning of line
### editing
`ctrl`+`p` Previous pattern completion
`ctrl`+`n` Next pattern completion
`ctrl`+`j` \<CR\> (Enter)
`ctrl`+`m` \<CR\>
`ctrl`+`t` indent current line
`ctrl`+`d` un-indent current line
`ctrl`+`r` then `<register>` insert register
## combination
Select inside function: `vi}`
Select inside function including parentheses: `va}`

Change a word: `ciw`
Change contents of a function: `ci{`
Change contents of a function including parentheses: `ca{`
Chang paragraph (or function): `cip`

Normal mode for just one command: `ctrl`+`o`
