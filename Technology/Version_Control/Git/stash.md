#git
[see and extract a file from stash](https://stackoverflow.com/questions/1105253/how-would-i-extract-a-single-file-or-changes-to-a-file-from-a-git-stash)

list stashed modifications:   `git stash list`
show latest stash [[Technology/Version_Control/Git/differences/diff]] :   `git stash show -p` 
push to stash:   `git stash`
pop from stash:   `git stash pop`
to apply changes from stash (while keeping them in stash):   `git stash apply`
remove all the stash entries:   `git stash clear`
remove a stash entry (use `list` see all):   `git stash drop stash@{1}`
see [[Technology/Version_Control/Git/differences/diff|diff]] vs stash:   `git diff stash@{0}^1 stash@{0}`
see [[Technology/Version_Control/Git/differences/diff|diff]] vs file_in_stash:   `git diff stash@{0}^1 stash@{0} -- <file_in_stash>`
checkout a file from stash:   `git checkout stash@{0} -- <file_in_stash>`
or to save it under another filename:
```shell
git show stash@{0}:<full filename>  >  <newfile>
```
or
```shell
git show stash@{0}:./<relative filename> > <newfile>
```
_note_ that here <full filename\> is full pathname of a file relative to top directory of a project (think: relative to `stash@{0}`)
You might need to protect `stash@{0}` from shell expansion, i.e. use `"stash@{0}"` or `'stash@{0}'`

push to stash while keeping the index:
```shell
git stash push -p -m "my commit message" --keep-index
```
- `-p` let's you select the hunks that should be stashed; whole files can be selected as well.
- `-m`  save a description to the stash entry
- If the `--keep-index` option is used, all changes already added to the index are left intact

#### stashing a commit from history:
[stack overflow](https://stackoverflow.com/questions/26884364/how-to-stash-my-previous-commit) [w3docs](https://www.w3docs.com/snippets/git/deleting-commits-from-a-branch-in-git.html)
1. Method A: [[reset]] to commit which we want to stash, then stash it
	1.  `git reset <SHA>`
	2.  `git stash push -m "commit to stash"`
	3. `git checout <SHA>` to the original HEAD location [[SHA]]
2. Method B: [[rebase|rebase -i]] to before the commit we want to stash. Then switch it to be the last commit. Then [[reset|reset --soft HEAD^]] and stash the index
	1. `git rebase -i HEAD~2`
	2. `reset --soft HEAD^`
	3. `stash push -m "commit to stash"`

#### applying several stashes:
If you applying 2 stashes and encounter merging conflicts between them (if they contain changes on the same file), stage the changes from the already applied stash, then apply the other stash.