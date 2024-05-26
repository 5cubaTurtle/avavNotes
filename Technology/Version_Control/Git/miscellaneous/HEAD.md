HEAD is the symbolic name for the currently checked out commit -- it's essentially what commit you're working on top of.
HEAD always points to the most recent commit which is reflected in the working tree. Most git commands which make changes to the working tree will start by changing HEAD.
Normally HEAD points to a branch name. When you commit, the status of the branch is altered and this change is visible through HEAD.

### Detaching HEAD
Detaching HEAD just means attaching it to a commit instead of a branch.
This is what it looks like beforehand:
	*HEAD -> main -> C1*
	![[Undetached_HEAD.png]]
 >The `*` here, means HEAD is pointing at the `main` branch.
 
After running `git checkout c1`, we get:
	*HEAD -> C1*
	![[detached_HEAD.png]]
see [[detached-HEAD-state]] for more info.
