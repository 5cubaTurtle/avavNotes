#git 
Refspec is a git notation for location that git can figure out (like the branch `foo` or even just `HEAD~1`).
### nothing as `<source>`
Git abuses the `<source>` parameter in two weird ways. These two abuses come from the fact that you can specify "nothing" as a valid `source` for both git push and git fetch. The way you specify nothing is via an empty argument:

- `git push origin :side` deletes the remote branch *side*. Not the local, if it exists.
- `git fetch origin :bugFix` creates a local branch *bugFix* at the location of `origin/main`.
