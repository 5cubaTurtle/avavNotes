#git 
This is a *.diff* file which contains the differences between 2 points in the tree.

diff patches are useful for:
- share changes via files
- Useful when changes are not ready for public branch
- Useful when collaborators do not share a remote

save diff to a file:`git diff 8527e7a e24cf05 > ~/Desktop/4_review.diff`
[[apply]] a patch to the working-directory:`git apply 4_review.diff`

**Note**: A patch can only be applied if the working-directory is in an acceptable 
state. Applying a diff could fail if the anchoring-lines are not present/different 
from what is expected. The working-dir doesn't need to match exactly to the 
working tree from which the diff was created, but any conflicted files have to match exactly.
