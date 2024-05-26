#git 
Reapply commits on top of another base tip

- Take commits from  a branch and reapply them at the end of another branch.
- Useful to integrate recent commits without merging.
- Maintains a cleaner, more linear project history.
- Ensures topic branch commits apply cleanly.

**Warning:**  The golden rule of `git rebase` is to never use it on _public_ branches. i.e don't rebase public branches since rebasing deletes the rebased branch.
### Usage
- rebase the current branch on top of *onto_branch*:   `git rebase onto_branch`
- rebase *new_feature* to tip of *onto_branch*: `git rebase onto_branch new_feature`, which is a short-hand of `git checkout new_feature` followed by `git rebase onto_branch`.
- To find the most recent common parent commit of two branches use the [[merge-base]] command.
- [interactive rebase](https://www.atlassian.com/git/tutorials/merging-vs-rebasing#conceptual-overview):   `git rebase -i main`, This will open a text editor listing all of the commits that are about to be moved. If the 2nd commit fixes a small problem in the 1st commit, you can condense them into a single commit with the `fixup` command:
```shell
pick 33d5b7a Message for commit #1
fixup 9480b3d Message for commit #2
pick 5c67e61 Message for commit #3
```

### Visual examples
#### Rebasing onto another branch
![[rebase0.png|450]]
Note the [[Technology/Version_Control/Git/miscellaneous/HEAD|HEAD]] is at `otherBran`.
`git rebase myBranch` yields:
![[rebase1.png|450]]
`rebase` applied all the commits of `otherBran` onto `myBranch`, including the commit `C5` which is not unique to `otherBran` but absent from the `myBranch`.
> To update `myBranch` to the latest commit (`C7`), rebase it onto `otherBran`:
> `git rebase myBranch otherBran`

#### Rebasing onto an older commit from the same branch
This could be used to reorder or exclude commits from history.
We rebasing interactively in this example.
![[rebase2.png]]
running `git rebase -i HEAD~4`. Then, in  reordering `C5` after `C2` and Omitting `C4` we get:
![[rebase3.png]]
This is useful since we could also squash several commits together using this technique.

### When to use rebase vs merge
- Merge to allow commits to stand out.
- Merge to bring large topic branches back into master.
- Rebase to add minor commits in master to a topic branch.
- Rebase to move commits from one branch to another.
- Merge anytime the topic branch is public and used by others.

### Handling Conflicts
- `git rebase --continue` (to next commit). Use this option after resolving any conflicts caused by `git rebase` applying a commit. This option says: "I've resolved conflicts from this commit. Commit it. Then continue to the next one. Keep going down the chain of commits which are being rebased."
- `git rebase --skip` (this commit, and go to next). All changes from this commit will be undone.
- `git rebase --abort` (the whole rebase).

### Rebasing onto non parent branches
We could use the `--onto` flag to specify from which commit to start counting the commits to rebase.
syntax: `git rebase --onto newbase upstream branch`. Here, the `upstream` element refers to parent branch. All commits after the `upstream` and up-to `branch` will be committed on-top of `newbase`. See the example in git rebase [[man]] (`man git rebase`) which uses the `--onto` flag.
The example from man:
![[rebase4.png]]
`git rebase --onto master next topic` yields the following tree:
![[rebase5.png]]
Without using the `--onto master` parameter, in this case, the whole branch *topic*(8 commits) would be rebased on-top of master.
### Undoing a rebase
- `git reset --hard`, this works unless [[ORIG_HEAD]] was changed (by another [[reset]], rebase or a [[merge]]).
- `git rebase --onto 9291f0c88 master new_feature` - undo by rebasing to former merge-base [[SHA]]. In fact, this could be used to move commits to any point in history.
	> After a rebase the old commits are still present for some time before being collected by [[git's-garbage-collector]].