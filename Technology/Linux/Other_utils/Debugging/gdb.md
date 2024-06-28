#linux 
The GNU Debugger

usage:`gdb a.out [core.file]`  (dont forget to compile with `-g` (debugging symbols))

some gdb commands (shortcut):
- `list 11`(`l`) show the code around line 11 
- `list 1,4` show the code around from line 1 to 4
- `list <func_name>` show the code of function named "func_name"
- `run`(`r`)  run the file 
- `kill`(`k`) stop the run
- `file` unload the file
- `file a.out` load the file
- `disassemble main` show assembly code of main
- `break 9`(`b 9`) set breakpoint at line 9 
- `tbreak 9` set temporary breakpoint at line 9 (deleted after 1st hit)
- `watch var` follow the value of the variable 'val'
- `info b` see all breakpoints and watches 
- `disable breakpoints [n]` disable breakpoint, watchpoint or catchpoint number 'n'. To see all breakpoints use `info b`
- `quit`(`q`) quit gdb 
- `print var`(`p var`) print the value of the variable named "var"
- `whatis var` show the type of "var"
- `next`(`n`) execute current line 
- `next 3`(`n 3`) execute 3 though the code (like next 3 times in a row)
- `step`(`s`) execute current line. If function then step into it.
- `where` print stack trace of the crash or where is current execution while debugging
- `continue`(`c`) execute until next breakpoint 
- `skip` Ignore a function while stepping
- `x ptr` print the memory at address "ptr"
- `x/d ptr` print the memory at address "ptr" in decimal base
- `x/5u ptr` print 5 words according to the type of "ptr". Present in unsigned decimal base
- `!` shell. To execute external shell command (i.e. !ls or !pwd)
- `dump memory <filname> <start_addr> <end_addr>` Write contents of memory to a file
  - example `dump memory file.dat ptr ptr+100` dump contents of program from address "ptr" and 100 bytes down the memory to file named "file.dat".

### how to print std::string
If you know that the string resides at e.g. 0x7fffffffda88, then:
`print *(char**)0x7fffffffda88`

### Cores
get core info: `file <core.####>`  
examine the trace of a core file  
`gdb exe core.file` then, in gdb, use the command `where`  

## [TUI](https://sourceware.org/gdb/current/onlinedocs/gdb/TUI-Overview.html#TUI-Overview)
