#vim 
#### Syntax:  
- :\[address\]s/old_text/new_text/  
#### Address components:
- `.` Current line
- `n` Line number n
- `.+m` m lines from current cursor position.
- `$` Last line
- `/string/` A line that contains "string"
- `%` Entire file
- `[addr1],[addr2]` Specifies a range

#### Examples:
- replace only the first occurrence of Banana with Kumquat in each of 11 lines starting with the current line (`.`) and continuing for the 10 that follow (`.+10`).  
	`:.,.+10s/Banana/Kumquat`  

- replace every occurrence (caused by the g at the end of the command) of apple with pear.  
	`:%s/apple/pear/g`  
- add a `|` to the end of every line marked by visual selection: mark all the wanted lines using `Shft`+`V`, then enter `'<,'>s/$/|`.
	- `$` in this context means the *end of line*, i.e. the *end of line* will be substituted for `$`
	 - The `'<,'>` is a visual selection range indicator in Vim. It represents the range of lines that you have visually selected using visual mode. `'<` indicates the start and `,'>` indicates the end of the visual selection.

- remove the last character from every line in the file. Use it if every line in the file ends with ^M as the result of a file transfer. Execute it when the cursor is on the first line of the file.  
	`:%s/.$//`
- remove first 5 characters of every line:  `:%s/^.\{0,5\}//g`
- substitute *new* for the **first** *old* in the current line`:s/old/new`
- substitute *new* for **all** *old*'s on a line:`:s/old/new/g`
- substitute phrases between two line *#*'s:`:#,#s/old/new/g`
- substitute all occurrences in the file:`:%s/old/new/g`
- ask for confirmation each time add 'c':`:%s/old/new/gc`
- delete lines not containing a pattern: `:g!/pattern/d`
	- `!` negation, to match lines the **do not** contain the pattern
	- `d` delete the matched lines
	- `g` command stands for global

Find all lines that match a pattern and do not match another pattern:
`:g/found/v/notfound/{cmd}`. This first finds all lines containing "`found`", but only executes `{cmd}` when there is no match for "`notfound`". See vim manual at *E147* (in vim do `:help E147`).
