#git 
Tracking branches are local references that have a direct relationship to an [[upstream-branch]].

When a local branch tracks a remote branch there are actually 3 branches to the process:
1. Branch on the remote repository "*remote*" branch (bugfix)
2. Local snapshot of the remote branch (origin/bugfix)
3. Local branch, tracking the remote branch (bugfix)
	remote-tracking branch is the 2nd one. git [[fetch]] synchronizes it with the actual remote branch (1).
 
see more at [git-pro book](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches)
## Expansion
Remote-tracking branches reflect the _state_ of remote repositories since you last talked([[fetch|git fetch]]) to those remote repositories. They help you understand the difference between your local work and what work is public.

Remote-tracking branches have the special property that when you check them out, you are put into a [[detached-HEAD-state]] . Git does this because you can't work on these branches directly; you have to work elsewhere and then share your work with the remote (after which your remote branches will be updated).

To be clear: Remote-tracking branches are on your _local_ repository, not on the remote repository.

remote-tracking branches also have a (required) naming convention -- they are displayed in the format of:

- `<remote name>/<branch name>`

Hence, if you look at a branch named `o/main`, the branch name is `main` and the name of the remote is `o`.

Most developers actually name their main remote `origin`, not `o`. This is so common that git actually sets up your remote to be named `origin` when you `git clone` a repository.

## Usage
- create a local branch which will track a remote branch use git [[checkout#create a tracking branch|checkout]]/[[branch#create a tracking branch|branch]].
- If you already have a local branch and want to set it to a remote branch you just pulled down, or want to change the upstream branch you’re tracking, you can use the `--set-upstream-to` option to [[branch#Set upstream|git branch]] to explicitly set it at any time.
- see what tracking branches you have set up:   `git branch -vv`

### Delete tracking reference:
Deleting a remote by [[push|push -d]] prunes the remote-tracking branch automatically.
However if, instead of me, a **collaborator** deletes the remote branch, we have to prune our remote-tracking reference using [[remote|remote prune]] command.
`git branch -rd <branch>`,   this will not delete the actual remote branch, only the local remote-tracking reference.
