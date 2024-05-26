#git 

Create, list, delete or verify a tag object signed with GPG

Tag specific points in a repository’s history as being important. Typically, people use this functionality to mark release points (`v1.0`, `v2.0` and so on). Tags never move as more commits are created. You can't "check out" a tag and then complete work on that tag -- tags exist as anchors in the commit tree that designate certain spots.

usage: `git tag <version_name> <ref>`, this will create a lightweight tag.
- `<ref>` could be anything Git could resolve to a commit - branch name for instance. If `<ref>` is omitted, the current commit will be tagged.

from [the Git website](https://git-scm.com/book/en/v2/Git-Basics-Tagging):
list all tags:   `git tag` or `git tag -l`
- `--list, -l` list the tags
- `-n#` list tags with # number of annotation lines
search for tags that match a particular pattern:   `git tag -l "v1.8.5*"`
- here `-l` is required to avoid creating a tag called "v1.8.5*"
see tags annotation use git [[show]]:   `git show v1.4`
to see the last tag on current branch use the [[describe]] command:   `git describe`
tags could be used instead of [[SHA]]'s by [[Technology/Version_Control/Git/differences/diff|git diff]]:`git diff v0.1..v1.1`

#### Create
create *annotated* (most common) tag on current  [[SHA]]:  `git tag -a v1.4 -m "my version 1.4"`
*lightweight* tag on current  [[SHA]]:   `git tag v1.4-lw`, lightweight tag contain no message.
- `-f` to force create a tag. If the same named tag was already created, you could force create it again on current commit with this flag.
tag a specific commit, use the commit-checksum( [[SHA]]):   `git tag -a v1.2 9fceb02`

#### Push
- [[push]] does not push the tags to remote by default
- [[fetch]] does fetches the tags by default
[[push]] a tag to remote server:   `git push origin <tagname>`
push all your tags:   `git push origin --tags`,  tags which aren't on the remote server will get transferred.

#### Delete
delete a tag locally:   `git tag -d v1.4-lw`
delete a tag on a remote:   `git push origin :refs/tags/v1.4-lw`
or   `git push origin --delete <tagname>`
- deleting a tag on the remote will **not** delete it locally

#### Checkout
you can [[checkout]] a tag:   `git checkout v2.0.0`. This will put you into a [[detached-HEAD-state]] since a tag is attached to a commit and not a branch. Thus, if you want to make changes to previous tag, you should create a branch ("version2") from this tag:
`git checkout -b version2 v2.0.0`
- this will create a new branch called *version2* attached to the previous branch at the commit of the tag *v2.0.0*.
