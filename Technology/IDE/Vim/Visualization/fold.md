#vim 
### References
`:help Folding`
quick reference: `:Q_fo`
[vim folding:](https://www.linux.com/training-tutorials/vim-tips-folding-fun/#:~:text=of%20open%20fold.-,Using%20folds,-Creating%20folds%20is)

### Frequently used
- `zf#j` creates a fold from the cursor down # lines. i.e: Fold 4 lines down: `zf4j`.
- `zf/string` creates a fold from the cursor to string.
- `zf` -> create fold. Also, [select a visual selection and then `zf` to fold it](https://www.linux.com/training-tutorials/vim-tips-folding-fun/#:~:text=enter%20visual%20mode%20using%20v%20or%20V%2C%20then%20select%20a%20few%20lines%20of%20text%20using%20the%20movement%20keys%2C%20and%20type%20zf)  
- `zfa}` -> :position the cursor on the first brace, and type `zfa}`
- `zj` moves the cursor to the next fold.
- `zk` moves the cursor to the previous fold.
- `zo` opens at the cursor.
- `zO` opens all at the cursor.
- `zm` increases the foldlevel by one.
- `zc` close at the cursor.
- `zM` closes all
- `zr` decreases the foldlevel by one.
- `zR` decreases the foldlevel to zero — all folds will be open.
- `zd` deletes the fold at the cursor.
- `zE` deletes all folds.
- `[z` move to start of open fold.
- `]z` move to end of open fold.
To see to it that Vim saves and restores folds when a file is closed and re-opened, add these two lines to your ~/.vimrc:
```vim
au BufWinLeave * mkview
au BufWinEnter * silent loadview
```
