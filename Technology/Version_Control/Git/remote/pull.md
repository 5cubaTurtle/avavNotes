#git 
updates the *working-directory* with changes from [[remote-repository]].
`git pull <remote> <refspec>`
Incorporates changes from a remote repository into the current branch.
### pull = fetch+merge
In its default mode, `git pull` is shorthand for [[fetch|git fetch]] followed by [[merge|git merge]] [[FETCH_HEAD]].

`git pull --rebase` is shorthand for a [[fetch]] and a [[rebase]]. This will not create a merging commit as with a regular `git pull`.
	- `--rebase` or `-r`
	- `--rebase=preserve` preserves the merge-commits on current branch.
	- `--rebase=interactive` starts interactive mode.

`git pull origin foo` is equal to:
`git fetch origin foo; git merge o/foo`

`git pull origin bar~1:bugFix` is equal to:
`git fetch origin bar~1:bugFix; git merge bugFix`

#### Illustration
##### not explicit args
![[pull0.png]]
`git pull origin main` yields:
![[pull1.png]]
By specifying `main` we downloaded commits onto `o/main` just as normal. Then we merged `o/main` to our currently checked out location which is _not_ the local branch `main`. For this reason it can actually make sense to run git pull multiple times (with the same args) from different locations in order to update multiple branches.
##### explicit args
![[pull2.png]]
`git pull origin main:foo` yields:
![[pull3.png]]
Git created a new branch locally named `foo`, downloaded commits from remote's main onto that branch `foo`, and then merged that branch into our currently checked out branch `bar`.
### more usage
force pull master from remote using [[fetch]] and [[reset]]:
```shell
git fetch --all
git branch backup_branch   # this is optional if you want to backup the difference from the remote branch
git reset --hard origin/master
```

`git pull` applies to **current** branch.
To pull from specific branch: `git pull 'remote-branch' 'branch-name'`
