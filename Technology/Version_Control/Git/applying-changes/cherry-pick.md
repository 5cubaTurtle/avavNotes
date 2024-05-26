#git 
Apply the changes introduced by some existing commits

apply single commit: `git cherry-pick b0f3f782a`
apply range of commit: `git cherry-pick b0f3f782a..f8d42c15f`
apply some commits to current branch:   `git cherry-pick b0f3f782a f8d42c15f 9e97d31a4 8083c9f68`
- `-n, --no-commit` apply the changes to working-tree w/o committing.
- `-e, --edit` edit the commit message. By default (w/o this option) the original message of the cherry-picked commit will be used.


**Note**: cherry-picking a merged commit cannot be done since git would not know which parent branch was used to merge. This info is needed for [[SHA]] building.

#### Visual example
Given the following tree, with HEAD on main:
![[cherry-pick0.png]]
`git cherry-pick C2 C4` yields:
![[cherry-pick1.png]]
Commits `C2` and `C4` plopped on-top of the HEAD.