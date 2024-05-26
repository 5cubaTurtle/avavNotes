#git 
Manage set of tracked repositories

Show a list of existing remotes   `git remote`
- `-v`  verbose, show remote url (for fetching and pushing)

Set local repo to remote tracking via HTTPS:
```shell
git remote add origin https://github.com/USERNAME/REPO.git
```
for example:  `git remote add origin https://github.com/ava10z/PythonSandbox.git

Set local repo to remote tracking via SSH:
```shell
git remote add origin git@github.com:USERNAME/REPO.git
```
for example:  `git remote add origin git@github.com:ava10z/PythonSandbox.git`

Set the repo to a new url use the `set-url` option:
```sh
git remote set-url origin git@bitbucket.org:bladeranger/llc_arduino
```

To see which remote branch is tracked check in the *.git/config* file.

To see all [[tracking]] branches:   `git remote show origin`

Useful for deleting [[stale]] **remote-tracking** branches. **Not** remote branches.
Delete remote-tracking references which are not tracking any remote branches (prune):  `git remote prune origin`
- `-n, --dry-run`   Do a test run. Do not remove anything; just report what it would remove.
- `-v, --verbose`   Report all removed objects.
	to delete individual reference use [[branch#Deleting|branch -r]]

### Note:
The [[prune|git prune]] command is not the same as `git remote prune` and typically should not be used.
