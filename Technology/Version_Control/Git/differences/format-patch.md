#git 
Prepare patches for e-mail submission.
This command produces *.patch* files. These are similar to the [[diff-patches]] but they also contain the metadata of the commit.

Some features of *.patch*:
- Export each commit in Unix mailbox format
- Useful for email distribution of changes
- Includes commit messages
- One commit per file by default

Export all commits in the range: `git format-patch 2e33f..655da`
Export all commits on current branch which are not in the master: `git format-patch master`
Export a single commit: `git format-patch -1 655da`
- The `-1` flag differentiate this command from the behavior of the previous one, where all commits up to the *665da* will be included.
Put patches files into a directory: `git format-patch master -o feature`
Output patches as a single file: `git format-patch 2e33f..655da --stdout > feature.patch`

**Note:** To apply the *format-patch* use the [[am]] command.
