#git
Download objects and refs from another repository

`git fetch` updates the **Local-repository** with changes from Remote-repository. In other words, it brings _local_ representation of the remote repository into synchronization with the _actual_ remote repository.
 
`git fetch` only updates [[tracking]] branches. Does not automatically [[prune]]s unless `-p` option was given. Unlike [[pull]], fetch does not promotes the HEAD pointer to the tip of the updated branch ([[FETCH_HEAD]]).

## Expansion
### git fetch w/o arguments
In the following illustration depicted a local *main* branch (left) and a remote *main* branch (right): 
![[fetch0.png]]
The `o/main` is the [[tracking]] branch of the remote `main` (right).
`git fetch` will update  `o/main` to the following state:
![[fetch1.png]]
Note that the local `main` still point to `C1` and thus became outdated. If instead of [[fetch|git fetch]], [[pull|git pull]] would have been used, then `main` would also be updated to `C3` which is the newest commit from the remote.

`git fetch` usually talks to the remote repository through the Internet (via a protocol like `http://` or `git://`).
`git fetch`, however, does not change anything about _your_ local state. It will not update your local non [[tracking]] branches or change anything about how your file system looks right now.

`git fetch` without arguments configured to fetch to all [[tracking]] branches.

### specify a remote and a branch
To fetch from a specific remote and branch use the following syntax:
	`git fetch <remote> <place>`

If you specify a place with git fetch like in the following command: `git fetch origin foo`, Git will go to the `foo` branch on the remote, grab all the commits that aren't present locally, and then plop them down onto the local [[tracking]] branch `origin/foo`.
![[fetch2.png]]
`git fetch origin foo` yields:
![[fetch3.png]]

### Explicitly fetching
Explicitly defining both the source and destination with `<source>:<destination>`:
If you feel passionate enough to fetch commits _directly_ onto a local branch, then yes you can specify that with a colon [[refspec]]. You can't fetch commits onto a branch that is checked out, but otherwise git will allow this.

Here is the only catch though -- `<source>` is now a place on the _remote_ and `<destination>` is a _local_ place to put those commits . It's the exact opposite of git push,.
That being said, developers rarely do this in practice.
Example:
![[fetch4.png]]
`git fetch origin foo~1:bar` will fetch `foo~1` directly into the local branch `bar`:
![[fetch5.png]]
From `foo~1`, `bar` is only missing `C2`. Thus only `C2` was downloaded to `bar`.
Note that no [[tracking]] branch was created for `bar` with this action. 
If `bar` doesn't exist at the time of this `fetch` command, git will create it.

## Examples
fetch all remotes:   `git fetch --all`
- `-p, --prune`  Before fetching, remove any [[tracking]] references that no longer exist on the remote. This could be set to always prune before fetch by [[Technology/Version_Control/Git/configuration/config|config]] command: `git config --global fetch.prune`.
- `--tags` fetch only [[tag]]s (with the necessary commits)

#### examples from man:
- Update the remote-tracking branches:`git fetch origin`
  The above command copies all branches from the remote refs/heads/ namespace and stores them to the local *refs/remotes/origin/* namespace, unless the *branch.\<name\>.fetch* option is used to specify a non-default *refspec*.

- Using [[refspec]]s explicitly: `git fetch origin +pu:pu maint:tmp`
  This updates (or creates, as necessary) branches `pu` and `tmp` in the local repository by fetching from the branches (respectively) `pu` and `maint` from the remote repository.
  The `pu` branch will be updated even if it does not fast-forward, because it is prefixed with a plus sign; `tmp` will not be.

- Peek at a remote’s branch, without configuring the remote in your local repository:
```shell
git fetch git://git.kernel.org/pub/scm/git/git.git maint
git log FETCH_HEAD
```
The first command fetches the `maint` branch from the repository at the [git-url](git://git.kernel.org/pub/scm/git/git.git) and the second command uses [[FETCH_HEAD]] to examine the branch with git-log(1). The fetched objects will eventually be removed by git’s built-in housekeeping (see git-gc(1)).