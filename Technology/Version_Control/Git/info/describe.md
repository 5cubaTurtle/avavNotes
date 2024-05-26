#git 
Give an object a human readable name based on an available ref

The command finds the most recent tag that is reachable from a commit.

syntax: `git describe <ref>`
- `<ref>` is anything Git can resolve to a commit. Without `<ref>` the current commit will be used.

The output of the command looks like:
`<tag>_<numCommits>_g<hash>`
Where `tag` is the closest ancestor tag in history, `numCommits` is how many commits away that tag is, and `<hash>` is the hash of the commit being described.