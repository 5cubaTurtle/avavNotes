#git 
Apply a series of patches from a [[format-patch|mailbox]].

- similar to cherry-picking, the patch contains the Author, the commit message, and the changes. It also transfers the commit history.

Apply a single patch: `git am feature/0001-some-name.patch`
Apply all patches in a directory: `git am feature/*.patch`
- this should apply the patches in a sequential order because, the patches are numbered in the beginning of the file name.
**Note**: unlike using [[apply]], *am* commits by default.
