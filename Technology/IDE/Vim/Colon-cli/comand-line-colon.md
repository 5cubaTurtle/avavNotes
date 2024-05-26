#vim 
### Examples
- `:w` - Save the file (write). See the [[file-operations|file-operations]] note.
- `:q` - Quit Vim.
- `:s/old/new/g` - Substitute "old" with "new" globally in the current line.
- `:set number` - Enable line numbering.
- `:g/pattern/d` - Delete all lines containing "pattern".
- `:!` - Display the [[stdout]]
- `:help` - Open Vim's built-in help.
- `:scriptnames` - Order of sourced files.
- `:so $MYVIMRC` resource the .vimrc during a running session.
### command line ":"
repeat last colon command:  
  `@:` and further repeats can be done with `@@`  

paste to command line from yank-register: `Ctrl+r` then `0`.  See this [SO](https://stackoverflow.com/questions/3997078/how-to-paste-yanked-text-into-the-vim-command-line) question.

### Variables
To save a variable:`:let var="Hello"`  
To print a variable:`:ec var`. This will expand and print the variable 'var'.  
To expand a variable in the command line use:`:exe "<command>" var`  
for example define vars:
```vim
:let bbp="/vstusr1/dev/csm/aaverma1/aaverma1_aaverma1_devsamlnx001_220199-Release/sam/bb/vst"
:let dlfile="dl/gn/src/dgn_ban_mig_classification.ppc"
```
Then use them:`:exe 'vs' bbp.dlfile`

