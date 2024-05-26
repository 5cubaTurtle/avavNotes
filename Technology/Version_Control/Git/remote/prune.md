#git 
Prune all unreachable objects from the object database

- `-n, --dry-run`   Do a test run. Do not remove anything; just report what it would remove.
- `-v, --verbose`   Report all removed objects.

### Note:
`git prune` is not the same as `git remote prune` and typically should not be used. It is part of git's garbage collection and could be directly called by `git gc`, but usually there is no need for it since its done automatically.