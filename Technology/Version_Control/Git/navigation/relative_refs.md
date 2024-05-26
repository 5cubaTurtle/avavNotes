#git
With relative refs, you can start somewhere memorable (like the branch `bugFix` or `HEAD`) and work from there.

Relative commits:
- Moving upwards one commit at a time with `^`
- Moving upwards a number of times with `~<num>`

### ^
Each time you append `^` to a ref name, you are telling Git to find the parent of the specified commit. So saying `main^` is equivalent to "the first parent of `main`". `main^^` is the grandparent (second-generation ancestor) of `main`.
Example:
![[carrot0.png]]
`git checkout main^` moves the [HEAD] to here:
![[carrot1.png]]
#### ^ with modifier
`^` could be used with a modifier. A modifier specifies which parent reference to follow from a merge commit. Remember that merge commits have multiple parents, so the path to choose is ambiguous. Git will normally follow the "first" parent upwards from a merge commit, but specifying a number with `^` changes this default behavior.
Given the following tree: 
![[carrot2.png]]
The `C3` commit has 2 parents.
To jump to the "first" parent (`C1`) use `git checkout HEAD^`.
To jump to the "second" parent (`C2`) use `git checkout HEAD^2`. Which would yield:
![[carrot3.png]]
### ~
The tilde operator (optionally) takes in a trailing number that specifies the number of parents you would like to ascend.
![[tilde0.png]]
`git checkout HEAD~4` will move the [HEAD] back 4 commits:
![[tilde1.png]]

### Combining relative refs
Given the following tree:
![[combination0.png]]
We could jump to `C3` using combination of relative refs: `git checkout HEAD^^2~2`
![[combination1.png]]