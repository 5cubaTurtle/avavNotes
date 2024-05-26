#git 
Join two or more development histories together

This operation will create a new commit on top of the current branch combining all commits (only the ones which are absent from the current branch) of the target branch.
Merge target branch:   `git merge <target>`

- `--no-commit`   merge the code without commiting. This allows further tweak the merge result before comitting. use `--no-ff` with `--no-commit` if merging a commit on the same trunk.

to merge the *main* branch into *feature* branch specified branches: `git merge feature main`. This creates a new "merge commit" in the *feature* branch.

merge in one commit:   `git merge --squash otherBranch`, this will sqash all commits of **otherBranch** into one and merge them into the current branch.

if there were conflicts during merge, run  `git merge --abort`, it will abort the merge process and try to reconstruct the pre-merge state.

**Warning:** Run `merge` only on "clean" (all changes committed) working tree.

#### Visual example
Given the tree:
![[merge0.png]]
Note that the [[Technology/Version_Control/Git/miscellaneous/HEAD|HEAD]](`*`) is at `main` branch.
After applying `git merge bugFix` we get:
![[merge1.png]]
`main` now points to a commit that has two parents. If you follow the arrows up the commit tree from `main`, you will hit every commit along the way to the root. This means that `main` contains all the work in the repository now.