#git 

`git log <branch>`
\<branch\> is current by default
flags
- `-n3, -3`   last 3 commits 
- `--since=YYYY-MM-DD`
- `--until=YYYY-MM-DD`
- `--grep="pattern"`
- `--oneline`   each log shown in single line
- `-p, --patch`   show diff for each log
- `--stat`   shows files changed and number of lines inserted and deleted
- `--graph`   shows graph of branches
- `--all` show all branches, even the umerged into the current one

Search for string *'bar'* in git history of file *foo.rb* ([SO](https://stackoverflow.com/a/10216050/5273667)): `git log -S'bar' -- foo.rb`,
or `git log -G'bar' -- foo.rb` to search for diff that contains 'bar' rather than for commits that changed number of occurrences of 'bar'.

List edits to lines 100-150 in *filename.txt*: `git log -L 100,150:filename.txt`

set a sprcific format using `--format="<formated string>"` (`-3`  displays only 3 lines):
```shell
git log -3 --format="%h - %an, %ar : %s"
f61749c8e - Avner A, 10 days ago : moved constants to file line_recogn...
dbaefd608 - Avner A, 12 days ago : added angles to print to logs
06869d183 - Avner A, 13 days ago : Merge branch 'master' of bitbucket.com:bla...
```
format specifiers:
- `%H`   Commit hash
- `%h`   Abbreviated commit hash
- `%T`   Tree hash
- `%t`   Abbreviated tree hash
- `%P`   Parent hashes
- `%p`   Abbreviated parent hashes
- `%an`   Author name ("Author" wrote the change)
- `%ae`   Author email
- `%ad`   Author date (format respects the --date=option)
- `%ar`   Author date, relative
- `%cn`   Committer name ("Committer" applied the change)
- `%ce`   Committer email
- `%cd`   Committer date
- `%cr`   Committer date, relative
- `%s`   Subject
- `%Cred`       switch color to red
- `%Cgreen`   switch color to green
- `%Cblue`     switch color to blue
- `%Creset`   reset color

useful log commad:`git log --format="%an %Cgreen%ar%Creset : %s" --graph`
after setting a named format via [[Technology/Version_Control/Git/configuration/config#default log behavior|config]] command, we could use it:
	`git log --format=<myFormat>`

Useful for visualizing branches:`git log --graph --all --decorate --oneline`