#git 
Apply a patch to files and/or to the index

- a "patch"  is a \*.diff file
apply a patch to the working-directory:`git apply 4_review.diff`
- `--index` apply to index as will as the working-dir
- `--cached` apply to index only
- `--check` Instead of applying the patch, see if the patch is applicable to the current working tree and/or the index file and detects errors.
- `-R, --reverse` Apply the patch in reverse.

**Note:** After applying the patches one still needs to commit them.