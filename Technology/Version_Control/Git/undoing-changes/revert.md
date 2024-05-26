#git 
Revert some existing commits

Given one or more existing commits, revert the changes that the related patches introduce, and record some new commits that record them. This requires your working tree to be clean (no modifications from the HEAD commit). This action creates a new commit.

While [[reset]]ting works great for local branches on your own machine, its method of "rewriting history" doesn't work for remote branches that others are using.
In order to reverse changes and _share_ those reversed changes with others, we need to use `git revert`.

revert a whole commit(by [[SHA]]):   `git revert 6794c13e52033cb5d8757`
- `--no-edit`  will use the default message when committing.
- `--no-commit, -n` will prevent creating a commit after reverting

revert a committed merge: `git revert -m 1 57b4e3eaa2b15633`
[detailed explanation](https://github.com/git/git/blob/master/Documentation/howto/revert-a-faulty-merge.txt)
- `-m parent-number, --mainline parent-number` Usually you cannot revert a merge because you do not know which side of the merge should be considered the mainline. This option specifies the parent number (starting from 1) of the mainline and allows revert to reverse the change relative to the specified parent.

   Reverting a merge commit declares that you will never want the tree changes brought in by the merge. As a result, later merges will only bring in tree changes introduced by
   commits that are not ancestors of the previously reverted merge. This may or may not be what you want.
   See the revert-a-faulty-merge How-To\[1\] for more details.

#### Visual example
![[revert0.png]]
`get revert HEAD` will yield:
![[revert1.png]]
The new commit `C2'` undoes the changes of the previous `C2` commit.