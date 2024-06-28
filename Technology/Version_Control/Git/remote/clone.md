#git
Clone a repository into a new directory

Clone a repo: `git clone https://url/to/the/repo`

### Branches when cloning
During a clone, git creates a remote branch for every branch on the remote (aka branches like `o/main`). It then creates a local branch that tracks the currently active branch on the remote, which is `main` in most cases.
