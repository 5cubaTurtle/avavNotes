#git 
List, create, or delete branches

list local branches:   `git branch`
- `-l`  Default. List the local branches
- `-lr` List the remote branches
- `-la` List all the branches
- `-l <pattern>`  show branches matching the pattern
- With `--contains`, shows only the branches that contain the named commit
- `--no-contains` inverts it.
- `--show-current` prints the current branch 
- `-v` or `-vv` will display tracking info among other

#### Create new branch
Create new branch:  `git branch <new_branch_name> [<ref>]`, this will **not** switch the HEAD to the newly created branch. To create and switch to the new branch use the [[switch|switch -c]] or the [[checkout|checkout -b]] command. If `<ref>` not provided, the branch will be created on current commit.

add `-v` for verbosity:   `git branch -v -v`, the 1st `-v` adds when was merged. The 2nd `-v` adds the [[tracking]] branch.
##### create a tracking branch
create a branch which tracks another branch:
	`git branch --track <branch_name> <branch_to_track>`
	 - `-t` is shorthand for `--track`
#### check merged branches
what branches merged into *some-branch*:  `git branch --merged some-branch`
- With `--merged`, only branches merged into the named commit will be listed.
- With `--no-merged` only branches not merged into the named commit will be listed.
	- If the \<commit\> argument is missing it defaults to HEAD
- `-r --merged` merged remote branches

#### Renaming
renaming a branch to a new-name: `git branch -m old-name new-name`
force-rename current branch to "new-branch":  `git branch -M <new-branch>`
- `-M`   is shortcut to `-m` and `--forced` allowing to renaming the branch even if the \<new-branch\> already exists.

#### Resetting
Reset a branch to a different commit: `git branch -f <branchname> <ref>`
- `-f`,  `--force` Reset \<branchname\> to \<startpoint\>, even if \<branchname\> exists already. Without `-f`, git branch refuses to change an existing branch. In combination with `-d` (or `--delete`), allow deleting the branch irrespective of its merged status. In combination with `-m` (or `--move`), allow renaming the branch even if the new branch name already exists, the same applies for `-c` (or `--copy`).

#### Copy
copying to a new named branch: `git branch -c new-branch`
- `-C` This will force copying over existing branch
#### Deleting
delete a branch:   `git branch -d <branch>`, add `-r` to delete the [[tracking]] branch as well. This will not delete the actual remote branch, only the local [[tracking]] one.
- `-D`   forced delete a branch if it is still not merged into the current branch
To delete the remote branch use [[push]]:   `git push origin -v --delete <branch>`
- `-d, --delete`  will delete the remote branch.
- `-v`  verbose
**Note**: a [good explenation](https://stackoverflow.com/questions/2003505/how-do-i-delete-a-git-branch-locally-and-remotely/23961231#23961231) for [[tracking]] branches.

#### Set upstream
Use current branch to track a [[upstream-branch|remote branch]]:
	`git branch --set-upstream-to=origin/remote_branch_name`
- `-u <upstream>, --set-upstream-to=<upstream>`   set the upstream
- `--unset-upstream`   stop tracking the remote
example:
```shell
$ git branch -u origin/serverfix
Branch serverfix set up to track remote branch serverfix from origin.
```

#### Troubleshoot
	Warning:  Your branch is based on 'origin/release', but the upstream is gone.
	  (use "git branch --unset-upstream" to fixup)
Explained in SOF, [here](https://stackoverflow.com/questions/21609781/why-call-git-branch-unset-upstream-to-fixup) and [here](https://stackoverflow.com/questions/37770467/why-do-i-have-to-git-push-set-upstream-origin-branch).
