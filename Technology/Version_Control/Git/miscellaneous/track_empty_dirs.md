#git 

Git will not track an empty directory. By convention the way to track an empty dir is to add the file .gitkeep to it:   `touch untrackrd/dir/path/.gitkeep`
To see all tracked files in a dir use the [[ls-tree]] command:   `git ls-tree HEAD`
