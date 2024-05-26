#git 

Switch branches
similar to "git [[checkout]] <branch\>"

`git switch <branch>`
create new branch:  `git switch -c <new-branch>`
- `-f, --force`   discard local changes (alias for `--discard-changes`)
- `-C <new-branch>, --force-create <new-branch>`   if \<new-branch\> exist, reset it to \<start-point\>

create a new branch off of a particular commit (SHA: 1a5ae0e):`git switch -c new_branch 1a5ae0e`