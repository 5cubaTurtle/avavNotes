[geeks4geeks](https://www.geeksforgeeks.org/bind-command-in-linux-with-examples/)
**bind** command is Bash shell builtin command. It is used to set Readline key bindings and variables. The keybindings are the keyboard actions that are bound to a function. So it can be used to change how the bash will react to keys or combinations of keys, being pressed on the keyboard.

**Syntax:**
```bash
bind [-lpsvPSVX] [-m keymap] [-q name] [-f filename] [-u name] [-r keyseq]
     [-x keyseq:shell-command] [keyseq:readline-function or readline-command]
```

**Options:**
- **-m keymap:** It uses KEYMAP as the key mapping scheme for the duration of the current command sequence. Acceptable keymap names are as follows : emacs, emacs-standard, emacs-meta, emacs-ctlx, vi, vi-move, vi-command, and vi-insert.
- **-l:** It list names of functions.
- **-P:** It list function names and bindings.
- **-p:** It list functions and bindings in a form that can be reused as input.
- **-S:** It list key sequences that invoke macros and their values.
- **-s:** It list key sequences that invoke macros and their values in a form that can be reused as input.
- **-V:** It list variable names and values.
- **-v:** It list variable names and values in a form that canbe reused as input.
- **-q function-name:** It query about which keys invoke the named function.
- **-u function-name:** It unbind all keys which are bound to the named function.
- **-r keyseq:** It remove the binding for KEYSEQ.
- **-f filename:** It read key bindings from FILENAME.
- **-x keyseq:shell-command:** It cause SHELL-COMMAND to be executed when KEYSEQ is entered.
- **-X**It lists key sequences bound with -x and associated commands in a form that can be reused as input.

### example
bind a key combination to a command ([[ls]] in this case): `bind '"\C-g":"ls\n"'`. This could be written to [[bashrc]] file to be set as default behavior for this key sequence.
