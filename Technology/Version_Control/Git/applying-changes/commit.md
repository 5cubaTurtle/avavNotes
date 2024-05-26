#git 

Record changes to the repository

**Note:** For modularity and collaboration's sake, commits should be as small as possible.

commit straight to repository:   `git commit -am`, (the `m` is for a short commit message). This commits **all staged** and all **tracked** files only. But **not** the untracked. So new files will **not** be committed.

stage files interactively before committing: `git commit -p`

amend previous commit   `git commit --amend`
**Note:** Only amend commits that are still local and have not been pushed somewhere. Amending previously pushed commits and force pushing the branch will cause problems for your collaborators. For more on what happens when you do this and how to recover if you’re on the receiving end read [The Perils of Rebasing](https://git-scm.com/book/en/v2/ch00/_rebase_peril).

commit hunks of changes interactively: `git commit -p path/to/file`
commit as different user:
```shell
git commit --author="Vitaly Bondar <vitaly.bondar@bladeranger.com>"
```
