#vim 

To move the cursor use one of the following key combinations.
`w` One word forward. `W` forward "big-word"
`b` Back one word. `B` back "big-word"
`%` jump to closing/opening bracket
`}` jump to next paragraph
`{` jump to last paragraph
`]m` jump to next *}*  (curly bracket) (usually a block in C++ code)
`[m` jump to previous *}*
`Ctrl`+`]` got to the [[ctags|tag]] under the cursor
`Ctrl`+`t` jump back a [[ctags|tag]]

Also the [[Technology/IDE/Vim/Search|Search]] moves the cursor.
### jumps
`:jumps` - to see the jump-list
`[n] Ctrl+o` - jump back (older) n times
`[n] Ctrl`+`i` - jump fwd (newer) n times
### line jump
`gg` or `H` Go start of file
`G` or `L` Go to last line
`M` Middle of view
`0` Beginning of line
`^` Beginning of line at first non whitespace character
`$` End of line
`:n` or `nG` Go to line n. Where `n` is the line number.
#### one character motions
`h` Back a character
`l` Forward a character
`j` Down a line
`k` Up a line
### markers
`ma` mark current location with mark **a**
`'a` jump to line marked by mark **a**
\`a jump to mark **a**
First and last characters of the last visual selection in the current buffer. In order to move the cursor to these marks, use the commands \`< and \`>, respectively (see :help \`> and :help \`<).
### character-seek on line
`f` Jump to next character on line:`f`*c* jumps to the next character *c*.
`F` Jump to previous character on line.
`t` Jump till the next character on line: `t`*c* will place the cursor before the following *c* character.
`T` Jump till the previous character on line.
 `;`/`,` Repeat latest character-seek forward/backward.

Goto file under cursor (`^` is the `Ctrl` key):  
-  `gf`
-  `^wf` or `^w^f`  - splits new window
-  `^wgf` - opens new tab
