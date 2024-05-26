#vim 

`:w` name Write edit buffer to file name  
`:wq` Write to file and quit  
`:q!` Quit without saving changes  
`ZZ` Same as :wq  
`:sh` Execute shell commands (`<ctrl>d`)  
`:e` Reload a file
`:e!` This will discard any changes made so far to the file 
`:w <differentName>`  save the file under different name
#### Read commands
`v`  expand [[visual-selection]] selection then `:w` *FILENAME* will save the visuall selection into the file named *FILENAME*.
`:r FILENAME` retrieves disk file FILENAME and puts it below the cursor position. w/o `FILENAME` the current file will be used.
`:r !dir` reads the output of the *dir* command and puts it below the cursor position.