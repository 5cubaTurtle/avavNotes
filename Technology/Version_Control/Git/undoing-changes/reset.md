#git 
Reset current HEAD to the specified state.

>**Warning:** This command changes the history as it moves the branch reference.

`reset` is able to move a branch reference in any direction, back in history or to some "future" point.
shift HEAD to previous commit:   `git reset HEAD~1`
reset changes to HEAD (working-tree and index):  `git reset --hard`
- `--soft`  Does not touch the index file or the working tree at all (but resets the head to \<commit\>, just like all modes do).
- `--mixed`  Default. Resets the index but not the working tree.
- `--hard` Resets the index and working tree. Any changes to tracked files in the working tree since \<commit\> are discarded.
- `--patch, -p` Interactively reset hunks of code

reset a file in the index to match the version in HEAD:   `git reset HEAD <file>`
Assuming the last commit hasn't been pushed, reset changes from before the last commit and **discard it from history**:
	`git reset --hard HEAD~1`

#### Visual example
Given the following tree:
![[reset0.png]]
`git reset HEAD^` will yield:
![[reset1.png]]
The main branch reference moved back to `C1`; now the local repository is in a state as if `C2` had never happened.