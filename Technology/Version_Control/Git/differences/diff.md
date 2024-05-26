#git 

`git diff`  by default shows the difference working-dir vs HEAD excluding whats been staged 

examples:
diff between <branch\> and working-dir:  `git diff <branch>`
diff vs 2 commits ago on the same branch:   `git diff HEAD~2`
diff vs 2 commits ago on the same branch for some file:   `git diff HEAD~2 filename`
diff between two previous commits in history:   `git diff e24ea93f0b0..4c47d53b18fe9`. The 2 commits are designated by their commit ids ([[SHA]]).
Or use HEAD pointer:   `git diff --color-words  HEAD~3..HEAD~1`

Some useful options:
- `--cached, --staged` diff between files/hunks which are staged and HEAD
- `--color-words`   color words instead of lines
- `--word-diff`   show diff by words instead of lines
- `--name-only`   list changed files

while in diff:
some controls as in [[less]], for example line wrap: `-` then `S`
