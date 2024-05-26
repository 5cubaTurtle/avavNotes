#vim 
compile current file: `:!g++ % -o %:r`  
- `%` refers to current file. `%:r` omits the prefix

to execute [[Makefile]] on current file:`:make %<`  
  - `%` will be substituted by the name of the currently opened file.
  - `<` after `%` removes extension and dot (foo.c => foo), so `%<` is the file name without extension.
  - if you currently in "file.cpp" and want to open "file.h", do:`:tabnew %<.h`