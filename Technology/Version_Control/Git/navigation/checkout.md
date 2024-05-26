#git 
Switch branches or restore working tree files

`git checkout [-q] [<branch>]`
- `-q`  quite, suppress feedback messages
- `-b`  create new branch and switch to it
- `-B`  create new branch if it doesn't exist
- `-m`  allows to merge the current branch with the destination. You will create a new [[branch]] for the merge
- `--patch, -p` interactively select the hunks of code to checkout

discard changes in working directory:  `git checkout -- <file>`
- `--`  means to checkout from current branch (from HEAD in this case)

get a file from a branch and save to work-tree and index: `git checkout <branch> <file>`

### create a tracking branch
To create a new branch which will track a "non-obvious" other branch:
```shell
$ git checkout -b sf origin/serverfix
Branch serverfix set up to track remote branch serverfix from origin.
Switched to a new branch 'sf'
```
This will create a new local branch `sf` which will track `origin/serverfix`.