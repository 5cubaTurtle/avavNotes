#git 

Update remote refs along with associated objects

## Expansion
`git push` is responsible for uploading _your_ changes to a specified remote and updating that remote to incorporate your new commits.
_note -- the behavior of `git push` with no arguments varies depending on one of git's settings called `push.default`. The default value for this setting depends on the version of git you're using_.

`git push`, git will figured out the remote _and_ the branch to push to by looking at the properties of the currently checked out branch ([[tracking]] branch). `git push` can optionally take arguments in the form of: `git push <remote> <place>`

To push explicitly: `git push origin main`

In English, this translates to:
_Go to the branch named `main` in my repository, grab all the commits, and then go to the branch `main` on the remote named `origin` and place whatever commits are missing on that branch._

By specifying `main` as the "place" argument, we told git where the commits will _come from_ and where the commits _will go_. It's essentially the "place" to synchronize between the two repositories.

> The command `git push origin main` ignores what is the currently checked-out since it is unambiguous.

In order to specify both the source and the destination of `<place>`, simply join the two together with a colon: `git push origin <source>:<destination>`. This is a colon [[refspec]].
example:
![[push2.png]]
`git push origin foo^:main` yields:
![[push3.png]]
Git resolved `foo^` into a location, uploaded whatever commits that weren't present yet on the remote, and then updated the destination.

What if the destination you want to push doesn't exist? No problem! Just give a branch name and git will create the branch on the remote for you.
![[push4.png]]
`git push origin main:newBranch` yields:
![[push5.png]]
Git also created the [[tracking]] branch locally.

## Examples
push w/o the pre-push hook: `git push --no-verify`
to push a tag: `git push origin <tagname>`

force push on a repo: `git push --force`
- use with **extreme** caution, collaborator's commits disappear, collaborator's subsequent commits are orphaned.
after performing forced push your collaborators have to run the [[reset]] command: `git reset --hard origin/main`, to synchronize their work-tree with the newly pushed commits. git [[pull]] will not be enough in this instance.

careful force push:   `git push --force-with-lease origin HEAD`
- `--force-with-lease`   If somebody else built on top of your original history while you are [[rebase|rebasing]], the tip of the branch at the remote may advance with her commit, and blindly pushing with `--force` will lose her work.

push a local branch to a remote branch:   
```shell
git push origin local-branch:remote-branch
```

To push on branch *doc-update* without checking out a branch:
	`git push origin HEAD:doc-update`

### Illustration
In the following image there is a local (left-side) and a remote (right) *main* branch.
![[push0.png]]
The local branch contains a new commit (`C2`) which is not updated to the main branch yet.
`git push` will publish the new commit to the remote repository:
![[push1.png]]
The remote received commit `C2`, the branch `main` on the remote was updated to point at `C2`, and the [[tracking|local reflection]] of the remote (`o/main`) was updated as well.
### delete remote branch:
- old way: `git push origin :<remote-branch>`
- new way:  `git push -d origin <remote-branch>`

### push a new branch:
If a branch with no upstream needs to be pushed:
   `git push --set-upstream origin <branch>`
   - `-u, --set-upstream`  For every branch that is up to date or successfully pushed, add upstream (tracking) reference, used by argument-less git-pull(1) and other commands. For more information, see **branch.\<name\>.merge** in **git-config(1)**.

### rename remote branch:
[[#delete remote branch|delete]] then [[#push a new branch| push a new one]]
